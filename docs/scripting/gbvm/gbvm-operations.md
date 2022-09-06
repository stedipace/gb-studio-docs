---
#
# This file is autogenerated. DO NOT MODIFY DIRECTLY
#
---

# GBVM Operations

## Core

### VM_STOP

```gbvm
VM_STOP
```
 Stops execution of context  

### VM_PUSH_CONST

```gbvm
VM_PUSH_CONST VAL
```
 Pushes immediate value to the top of the VM stack  
- **VAL**:  immediate value to be pushed  

### VM_POP

```gbvm
VM_POP N
```
 Removes the top values from the VM stack  
- **N**:  number of values to be removed from the stack  

### VM_CALL

```gbvm
VM_CALL ADDR
```
 Call script by near address  
- **ADDR**:  address of the script subroutine  

### VM_RET

```gbvm
VM_RET
```
 Returns from the near call  

### VM_RET_N

```gbvm
VM_RET_N N
```
 Returns from the near call and clear N arguments on stack  
- **N**:  number of arguments to be removed from the stack  

### VM_GET_FAR

```gbvm
VM_GET_FAR IDX, SIZE, BANK, ADDR
```
 Get byte or word by the far pointer into variable  
- **IDX**:  Target variable  
- **SIZE**:  Size of the ojject to be acquired:  
`.GET_BYTE`  - get 8-bit value  
`.GET_WORD`  - get 16-bit value  
- **BANK**:  Bank number of the object  
- **ADDR**:  Address of the object  

### VM_LOOP

```gbvm
VM_LOOP IDX, LABEL, N
```
 Loops while variable is not zero, by the near address  
- **IDX**:  Loop counter variable  
- **LABEL**:  Jump label for the next iteration  
- **N**:  amount of values to be removed from stack on exit  

### .CASE

```gbvm
.CASE VAL, LABEL
```
### VM_SWITCH

```gbvm
VM_SWITCH IDX, SIZE, N
```
 Compares variable with a set of values, and if equal jump to the specified label.  
values for testing may be defined with the .CASE macro, where VAL parameter is a value for testing and LABEL is a jump label  
- **IDX**:  variable for compare  
- **SIZE**:  amount of entries for test.  
- **N**:  amount of values to de cleaned from stack on exit  

### VM_JUMP

```gbvm
VM_JUMP LABEL
```
 Jumps to near address  
- **ARG0**:  jump label  

### VM_CALL_FAR

```gbvm
VM_CALL_FAR BANK, ADDR
```
 Call far routine (inter-bank call)  
- **BANK**:  Bank number of the routine  
- **ADDR**:  Address of the routine  

### VM_RET_FAR

```gbvm
VM_RET_FAR
```
 Return from the far call  

### VM_RET_FAR_N

```gbvm
VM_RET_FAR_N N
```
 Return from the far call and remove N arguments from stack  
- **N**:  Number of arguments to be removed from stack  

### VM_INVOKE

```gbvm
VM_INVOKE BANK, ADDR, N, PARAMS
```
 Invokes C function until it returns true.  
- **BANK**:  Bank number of the function  
- **ADDR**:  Address of the function, currently 2 functions are implemented:  
`_wait_frames`   - wait for N vblank intervals  
`_camera_shake`  - shake camera N times  
- **N**:  Number of arguments to be removed from stack on return  
- **PARAMS**:  Points the first parameter to be passed into the C function  

### VM_BEGINTHREAD

```gbvm
VM_BEGINTHREAD BANK, THREADPROC, HTHREAD, NARGS
```
 Spawns a thread in a separate context  
- **BANK**:  Bank number of a thread function  
- **THREADPROC**:  Address of a thread function  
- **HTHREAD**:  Variable that receives the thread handle  
- **NARGS**:  Amount of values from the stack to be copied into the stack of the new context  

### VM_IF

```gbvm
VM_IF CONDITION, IDXA, IDXB, LABEL, N
```
 Compares two variables using for condition.  
- **CONDITION**:  Condition for test:  
`.EQ`   - variables are equal  
`.LT`   - A is lower than B  
`.LTE`  - A is lower or equal than B  
`.GT`   - A is greater than B  
`.GTE`  - A is greater or equal than B  
`.NE`   - A is not equal to B  
- **IDXA**:  A variable  
- **IDXB**:  B variable  
- **LABEL**:  Jump label when result is TRUE  
- **N**:  Number of values to be removed from stack if the result is true  

### VM_PUSH_VALUE_IND

```gbvm
VM_PUSH_VALUE_IND IDX
```
 Pushes a value on VM stack or a global indirectly from an index in the variable  
- **IDX**:  variable that contains the index of the variable to be pushed on stack  

### VM_PUSH_VALUE

```gbvm
VM_PUSH_VALUE IDX
```
 Pushes a value of the variable onto stack  
- **IDX**:  variable to be pushed  

### VM_RESERVE

```gbvm
VM_RESERVE N
```
 Reserves or disposes amount of values on stack  
- **N**:  positive value - amount of variables to be reserved on stack, negative value - amount of variables to be popped from stack  

### VM_SET

```gbvm
VM_SET IDXA, IDXB
```
 Assigns variable B to variable A  
- **IDXA**:  Variable A  
- **IDXB**:  Variable B  

### VM_SET_CONST

```gbvm
VM_SET_CONST IDX, VAL
```
 Assigns immediate value to the variable  
- **IDX**:  Target variable  
- **VAL**:  Source immediate value  

### VM_RPN

```gbvm
VM_RPN
```
 Reverse Polish Notation (RPN) calculator, returns result(s) on the VM stack  

### .R_INT8

```gbvm
.R_INT8 ARG0
```
### .R_INT16

```gbvm
.R_INT16 ARG0
```
### .R_REF

```gbvm
.R_REF ARG0
```
### .R_REF_IND

```gbvm
.R_REF_IND ARG0
```
### .R_REF_SET

```gbvm
.R_REF_SET ARG0
```
### .R_OPERATOR

```gbvm
.R_OPERATOR ARG0
```
### .R_STOP

```gbvm
.R_STOP
```
### VM_JOIN

```gbvm
VM_JOIN IDX
```
 Joins a thread  
- **IDX**:  Thread handle for joining  

### VM_TERMINATE

```gbvm
VM_TERMINATE IDX
```
 Kills a thread  
- **IDX**:  Thread handle for killing  

### VM_IDLE

```gbvm
VM_IDLE
```
 Signals thread runner, that context is in a waitable state  

### VM_GET_TLOCAL

```gbvm
VM_GET_TLOCAL IDXA, IDXB
```
 Gets thread local variable.  
- **IDXA**:  Target variable  
- **IDXB**:  Thread local variable index  

### VM_IF_CONST

```gbvm
VM_IF_CONST CONDITION, IDXA, B, LABEL, N
```
 Compares a variable to an immediate value  
- **CONDITION**:  Condition for test:  
`.EQ`   - variables are equal  
`.LT`   - A is lower than B  
`.LTE`  - A is lower or equal than B  
`.GT`   - A is greater than B  
`.GTE`  - A is greater or equal than B  
`.NE`   - A is not equal to B  
- **IDXA**:  A variable  
- **B**:  immediate value to be compared with  
- **LABEL**:  Jump label when result is TRUE  
- **N**:  Number of values to be removed from stack if the result is true  

### VM_GET_UINT8

```gbvm
VM_GET_UINT8 IDXA, ADDR
```
 Gets unsigned int8 from WRAM  
- **IDXA**:  Target variable  
- **ADDR**:  Address of the unsigned 8-bit value in WRAM  

### VM_GET_INT8

```gbvm
VM_GET_INT8 IDXA, ADDR
```
 Gets signed int8 from WRAM  
- **IDXA**:  Target variable  
- **ADDR**:  Address of the signed 8-bit value in WRAM  

### VM_GET_INT16

```gbvm
VM_GET_INT16 IDXA, ADDR
```
 Gets signed int16 from WRAM  
- **IDXA**:  Target variable  
- **ADDR**:  Address of the signed 16-bit value in WRAM  

### VM_SET_UINT8

```gbvm
VM_SET_UINT8 ADDR, IDXA
```
 Sets unsigned int8 in WRAM from variable  
- **ADDR**:  Address of the unsigned 8-bit value in WRAM  
- **IDXA**:  Source variable  

### VM_SET_INT8

```gbvm
VM_SET_INT8 ADDR, IDXA
```
 Sets signed int8 in WRAM from variable  
- **ADDR**:  Address of the signed 8-bit value in WRAM  
- **IDXA**:  Source variable  

### VM_SET_INT16

```gbvm
VM_SET_INT16 ADDR, IDXA
```
 Sets signed int16 in WRAM from variable  
- **ADDR**:  Address of the signed 16-bit value in WRAM  
- **IDXA**:  Source variable  

### VM_SET_CONST_INT8

```gbvm
VM_SET_CONST_INT8 ADDR, V
```
 Sets signed int8 in WRAM to the immediate value  
- **ADDR**:  Address of the signed 8-bit value in WRAM  
- **V**:  Immediate value  

### VM_SET_CONST_UINT8

```gbvm
VM_SET_CONST_UINT8 ADDR, V
```
 Sets unsigned int8 in WRAM to the immediate value  
- **ADDR**:  Address of the unsigned 8-bit value in WRAM  
- **V**:  Immediate value  

### VM_SET_CONST_INT16

```gbvm
VM_SET_CONST_INT16 ADDR, V
```
 Sets signed int16 in WRAM to the immediate value  
- **ADDR**:  Address of the signed 16-bit value in WRAM  
- **V**:  Immediate value  

### VM_INIT_RNG

```gbvm
VM_INIT_RNG IDX
```
 Initializes RNG seed with the value from the variable  
- **IDX**:  Seed value  

### VM_RANDOMIZE

```gbvm
VM_RANDOMIZE
```
 Initializes RNG seed  

### VM_RAND

```gbvm
VM_RAND IDX, MIN, LIMIT
```
 Returns random value between MIN and MIN + LIMIT  
- **IDX**:  Target variable  
- **MIN**:  Minimal random value  
- **LIMIT**:  range of the random values  

### VM_LOCK

```gbvm
VM_LOCK
```
 Disable switching of VM threads  

### VM_UNLOCK

```gbvm
VM_UNLOCK
```
 Enable switching of VM threads  

### VM_RAISE

```gbvm
VM_RAISE CODE, SIZE
```
 Raises an exception  
- **CODE**:  Exception code:  
`EXCEPTION_RESET`        - Resets the device.  
`EXCEPTION_CHANGE_SCENE` - Changes to a new scene.  
`EXCEPTION_SAVE`         - Saves the state of the game.  
`EXCEPTION_LOAD`         - Loads the saved state of the game.  
- **SIZE**:  Length of the parameters to be passed into the exception handler  

### VM_SET_INDIRECT

```gbvm
VM_SET_INDIRECT IDXA, IDXB
```
 Assigns variable that is addressed indirectly to the other variable  
- **IDXA**:  Variable that contains the index of the target variable  
- **IDXB**:  Source variable that contains the value to be assigned  

### VM_GET_INDIRECT

```gbvm
VM_GET_INDIRECT IDXA, IDXB
```
 Assigns a variable to the value of variable that is addressed indirectly  
- **IDXA**:  Target variable  
- **IDXB**:  Variable that contains the index of the source variable  

### VM_TEST_TERMINATE

```gbvm
VM_TEST_TERMINATE FLAGS
```
 Terminates unit-testing immediately  
- **FLAGS**:  terminate flags:  
`.TEST_WAIT_VBL` wait for VBlank before terminating  

### VM_POLL_LOADED

```gbvm
VM_POLL_LOADED IDX
```
 Checks that VM state was restored and reset the restore flag  
- **IDX**:  Target result variable  

### VM_PUSH_REFERENCE

```gbvm
VM_PUSH_REFERENCE IDX
```
 Translates IDX into absolute index and pushes result to VM stack  
- **IDX**:  index of the variable  

### VM_CALL_NATIVE

```gbvm
VM_CALL_NATIVE BANK, PTR
```
 Calls native code by the far pointer  
- **BANK**:  Bank number of the native routine  
- **PTR**:  Address of the native routine  

### VM_MEMSET

```gbvm
VM_MEMSET DEST, VALUE, COUNT
```
 Clear VM memory  
- **DEST**:  First variable to be cleared  
- **VALUE**:  Variable containing the value to be filled with  
- **COUNT**:  Number of variables to be filled  

### VM_MEMCPY

```gbvm
VM_MEMCPY DEST, SOUR, COUNT
```
 copy VM memory  
- **DEST**:  First destination variable  
- **SOUR**:  First source variable  
- **COUNT**:  Number of variables to be copied  

## Actor

### VM_ACTOR_MOVE_TO

```gbvm
VM_ACTOR_MOVE_TO IDX
```
 Move actor to the new position  
- **IDX**:  points to the beginning of the pseudo-structure that contains these members:  
`ID`   - Actor number  
`X`    - New X-coordinate of the actor  
`Y`    - New Y-coordinate of the actor  
`ATTR` - Bit flags:  
`.ACTOR_ATTR_H_FIRST`    - move horizontal first  
`.ACTOR_ATTR_CHECK_COLL` - respect collisions  
`.ACTOR_ATTR_DIAGONAL`   - allow diagonal movement  

### VM_ACTOR_MOVE_CANCEL

```gbvm
VM_ACTOR_MOVE_CANCEL ACTOR
```
 Cancel movement of actor  
- **ACTOR**:  Variable that contains the actor number  

### VM_ACTOR_ACTIVATE

```gbvm
VM_ACTOR_ACTIVATE ACTOR
```
 Activate the actor  
- **ACTOR**:  Variable that contains the actor number  

### VM_ACTOR_SET_DIR

```gbvm
VM_ACTOR_SET_DIR ACTOR, DIR
```
 Set direction of the actor  
- **ACTOR**:  Variable that contains the actor number  
- **DIR**:  one of these directions:  
`.DIR_DOWN`   - actor faces down  
`.DIR_RIGHT`  - actor faces right  
`.DIR_UP`     - actor faces up  
`.DIR_LEFT`   - actor faces left  

### VM_ACTOR_DEACTIVATE

```gbvm
VM_ACTOR_DEACTIVATE ACTOR
```
 Deactivate the actor  
- **ACTOR**:  Variable that contains the actor number  

### VM_ACTOR_SET_ANIM

```gbvm
VM_ACTOR_SET_ANIM ACTOR, ANIM
```
 Set actor animation  
- **ACTOR**:  Variable that contains the actor number  
- **ANIM**:  Animation number  

### VM_ACTOR_SET_POS

```gbvm
VM_ACTOR_SET_POS IDX
```
 Set new actor position  
- **IDX**:  points to the beginning of the pseudo-structure that contains these members:  
`ID`   - Actor number  
`X`    - New X-coordinate of the actor  
`Y`    - New Y-coordinate of the actor  

### VM_ACTOR_EMOTE

```gbvm
VM_ACTOR_EMOTE ACTOR, AVATAR_BANK, AVATAR
```
 Set actor emotion  
- **ACTOR**:  Variable that contains the actor number  
- **AVATAR_BANK**:  Bank of the avatar image  
- **AVATAR**:  Address of the avatar image  

### VM_ACTOR_SET_BOUNDS

```gbvm
VM_ACTOR_SET_BOUNDS ACTOR, LEFT, RIGHT, TOP, BOTTOM
```
 Set actor bounding box  
- **ACTOR**:  Variable that contains the actor number  
- **LEFT**:  Left boundary of the bounding box  
- **RIGHT**:  Right boundary of the bounding box  
- **TOP**:  Top boundary of the bounding box  
- **BOTTOM**:  Bottom boundary of the bounding box  

### VM_ACTOR_SET_SPRITESHEET

```gbvm
VM_ACTOR_SET_SPRITESHEET ACTOR, SHEET_BANK, SHEET
```
 Set actor spritesheet  
- **ACTOR**:  Variable that contains the actor number  
- **SHEET_BANK**:  Bank of the sprite sheet  
- **SHEET**:  Address of the sprite sheet  

### VM_ACTOR_SET_SPRITESHEET_BY_REF

```gbvm
VM_ACTOR_SET_SPRITESHEET_BY_REF ACTOR, FAR_PTR
```
 Set actor spritesheet using far the pointer in variables  
- **ACTOR**:  Variable that contains the actor number  
- **FAR_PTR**:  points to the pseudo-struct that contains the address of the sprite sheet:  
`BANK` - Bank of the sprite sheet  
`DATA` - Address of the sprite sheet  

### VM_ACTOR_REPLACE_TILE

```gbvm
VM_ACTOR_REPLACE_TILE ACTOR, TARGET_TILE, TILEDATA_BANK, TILEDATA, START, LEN
```
 Replace tile in the actor spritesheet  
- **ACTOR**:  Variable that contains the actor number  
- **TARGET_TILE**:  Tile number for replacement  
- **TILEDATA_BANK**:  Bank of the tile data  
- **TILEDATA**:  Address of the tile data  
- **START**:  Start tile in the tile data array  
- **LEN**:  Amount of tiles for replacing  

### VM_ACTOR_GET_POS

```gbvm
VM_ACTOR_GET_POS IDX
```
 Get actor position  
- **IDX**:  points to the beginning of the pseudo-structure that contains these members:  
`ID`   - Actor number  
`X`    - X-coordinate of the actor  
`Y`    - Y-coordinate of the actor  

### VM_ACTOR_GET_DIR

```gbvm
VM_ACTOR_GET_DIR IDX, DEST
```
 Get direction of the actor  
- **IDX**:  Variable that contains the actor number  
- **DEST**:  Target variable that receive the actor direction  

### VM_ACTOR_GET_ANGLE

```gbvm
VM_ACTOR_GET_ANGLE IDX, DEST
```
 Get actor angle  
- **IDX**:  Variable that contains the actor number  
- **DEST**:  Target variable that receive the actor angle  

### VM_ACTOR_SET_ANIM_TICK

```gbvm
VM_ACTOR_SET_ANIM_TICK ACTOR, TICK
```
 Set actor animation tick  
- **ACTOR**:  Variable that contains the actor number  
- **TICK**:  Animation tick  

### VM_ACTOR_SET_MOVE_SPEED

```gbvm
VM_ACTOR_SET_MOVE_SPEED ACTOR, SPEED
```
 Set actor move speed  
- **ACTOR**:  Variable that contains the actor number  
- **SPEED**:  Actor move speed  

### VM_ACTOR_SET_FLAGS

```gbvm
VM_ACTOR_SET_FLAGS ACTOR, FLAGS, MASK
```
 Set actor flags  
- **ACTOR**:  Variable that contains the actor number  
- **FLAGS**:  bit values to be set or cleared:  
`.ACTOR_FLAG_PINNED`      - pin/unpin the actor  
`.ACTOR_FLAG_HIDDEN`      - hide/show actor  
`.ACTOR_FLAG_ANIM_NOLOOP` - disable animation loop  
`.ACTOR_FLAG_COLLISION`   - disable/enable collision  
`.ACTOR_FLAG_PERSISTENT`  - set persistent actor flag  
- **MASK**:  bit mask of values to be set or cleared  

### VM_ACTOR_SET_HIDDEN

```gbvm
VM_ACTOR_SET_HIDDEN ACTOR, HIDDEN
```
 Hide/show actor  
- **ACTOR**:  Variable that contains the actor number  
- **HIDDEN**:  `.ACTOR_VISIBLE` shows actor, `.ACTOR_HIDDEN` hides the actor  

### VM_ACTOR_SET_COLL_ENABLED

```gbvm
VM_ACTOR_SET_COLL_ENABLED ACTOR, ENABLED
```
 Enable/disable actor collisions  
- **ACTOR**:  Variable that contains the actor number  
- **ENABLED**:  `.ACTOR_COLLISION_DISABLED` disables actor collision, `.ACTOR_COLLISION_ENABLED` enables actor collision  

### VM_ACTOR_TERMINATE_UPDATE

```gbvm
VM_ACTOR_TERMINATE_UPDATE ACTOR
```
 Terminates the actor update script  
- **ACTOR**:  Variable that contains the actor number  

### VM_ACTOR_SET_ANIM_FRAME

```gbvm
VM_ACTOR_SET_ANIM_FRAME ACTOR
```
 Set animation frame for the actor  
- **ACTOR**:  pseudo-struct that contains these members:  
`ID`    - Actor number  
`FRAME` - Animation frame  

### VM_ACTOR_GET_ANIM_FRAME

```gbvm
VM_ACTOR_GET_ANIM_FRAME ACTOR
```
 Get animation frame of the actor  
- **ACTOR**:  pseudo-struct that contains these members:  
`ID`    - Actor number  
`FRAME` - Animation frame  

### VM_ACTOR_SET_ANIM_SET

```gbvm
VM_ACTOR_SET_ANIM_SET ACTOR, OFFSET
```
 Set animation frame for the actor  
- **ACTOR**:  Variable that contains the actor number  
- **OFFSET**:  Animation set number  

## Camera

### VM_CAMERA_MOVE_TO

```gbvm
VM_CAMERA_MOVE_TO IDX, SPEED, AFTER_LOCK
```
 Moves the camera to the new position  
- **IDX**:  Start of the pseudo-structure which contains the new camera position:  
`X` - X-coordinate of the camera position  
`Y` - Y-coordinate of the camera position  
- **SPEED**:  Speed of the camera movement  
- **AFTER_LOCK**:  Lock status of the camera after the movement  
`.CAMERA_LOCK`   - lock camera by X and Y  
`.CAMERA_LOCK_X` - lock camera by X  
`.CAMERA_LOCK_Y` - lock camera by Y  
`.CAMERA_UNLOCK` - unlock camera  

### VM_CAMERA_SET_POS

```gbvm
VM_CAMERA_SET_POS IDX
```
 Sets the camera position  
- **IDX**:  Start of the pseudo-structure which contains the new camera position:  
`X` - X-coordinate of the camera position  
`Y` - Y-coordinate of the camera position  

## Color

### .DMG_PAL

```gbvm
.DMG_PAL COL1, COL2, COL3, COL4
```
### .CGB_PAL

```gbvm
.CGB_PAL R1,G1,B1 R2,G2,B2 R3,G3,B3 R4,G4,B4
```
### VM_LOAD_PALETTE

```gbvm
VM_LOAD_PALETTE MASK, OPTIONS
```
## Game Boy

### VM_LOAD_TILES

```gbvm
VM_LOAD_TILES ID, LEN, BANK, ADDR
```
### VM_LOAD_TILESET

```gbvm
VM_LOAD_TILESET IDX, BANK, BKG
```
Loads a new tileset into the background VRAM tiles starting at a given tile id (`IDX`).  

### VM_SET_SPRITE_VISIBLE

```gbvm
VM_SET_SPRITE_VISIBLE MODE
```
### VM_SHOW_SPRITES

```gbvm
VM_SHOW_SPRITES
```
### VM_HIDE_SPRITES

```gbvm
VM_HIDE_SPRITES
```
### VM_INPUT_WAIT

```gbvm
VM_INPUT_WAIT MASK
```
### VM_INPUT_ATTACH

```gbvm
VM_INPUT_ATTACH MASK, SLOT
```
### VM_INPUT_GET

```gbvm
VM_INPUT_GET IDX, JOYID
```
### VM_CONTEXT_PREPARE

```gbvm
VM_CONTEXT_PREPARE SLOT, BANK, ADDR
```
### VM_OVERLAY_SET_MAP

```gbvm
VM_OVERLAY_SET_MAP IDX, X_IDX, Y_IDX, BANK, BKG
```
### VM_GET_TILE_XY

```gbvm
VM_GET_TILE_XY TILE_IDX, X_IDX, Y_IDX
```
### VM_REPLACE_TILE

```gbvm
VM_REPLACE_TILE TARGET_TILE_IDX, TILEDATA_BANK, TILEDATA, START_IDX, LEN
```
### VM_POLL

```gbvm
VM_POLL IDX_EVENT, IDX_VALUE, MASK
```
### VM_SET_SPRITE_MODE

```gbvm
VM_SET_SPRITE_MODE MODE
```
### VM_REPLACE_TILE_XY

```gbvm
VM_REPLACE_TILE_XY X, Y, TILEDATA_BANK, TILEDATA, START_IDX
```
### VM_INPUT_DETACH

```gbvm
VM_INPUT_DETACH MASK
```
## GB Printer

### VM_PRINTER_DETECT

```gbvm
VM_PRINTER_DETECT ERROR, DELAY
```
 Detect printer  
- **ERROR**:  Target variable that receives the result of detection  
- **DELAY**:  Detection timeout  

### VM_PRINT_OVERLAY

```gbvm
VM_PRINT_OVERLAY ERROR, START, HEIGHT, MARGIN
```
 Print up to HEIGHT rows of the overlay window (must be multiple of 2)  
- **ERROR**:  Target variable that receives the result of printing  
- **START**:  Start line of the overlay window  
- **HEIGHT**:  Amount of lines to print  
- **MARGIN**:  Lines to feed after the printing is finished  

## Load and Save

### .SAVE_SLOT

```gbvm
.SAVE_SLOT SLOT
```
### VM_SAVE_PEEK

```gbvm
VM_SAVE_PEEK RES, DEST, SOUR, COUNT, SLOT
```
 Reads variables from the save slot  
- **RES**:  Result of the operation  
- **DEST**:  First destination variable to be read into  
- **SOUR**:  First source variable in the save slot  
- **COUNT**:  Number of variables to be read  
- **SLOT**:  Save slot number  

### VM_SAVE_CLEAR

```gbvm
VM_SAVE_CLEAR SLOT
```
 Erases data in save slot  
- **SLOT**:  Slot number  

## Math

### VM_SIN_SCALE

```gbvm
VM_SIN_SCALE IDX, IDX_ANGLE, SCALE
```
### VM_COS_SCALE

```gbvm
VM_COS_SCALE IDX, IDX_ANGLE, SCALE
```
## Music and Sound

### VM_MUSIC_PLAY

```gbvm
VM_MUSIC_PLAY TRACK_BANK, TRACK, LOOP
```
 Starts playing of music track  
- **BANK**:  Bank number of the track  
- **ADDR**:  Address of the track  
- **LOOP**:  If the track will loop on end (`.MUSIC_LOOP`) or not (`.MUSIC_NO_LOOP`)  

### VM_MUSIC_STOP

```gbvm
VM_MUSIC_STOP
```
 Stops playing of music track  

### VM_MUSIC_MUTE

```gbvm
VM_MUSIC_MUTE MASK
```
 Mutes/unmutes mysic channels.  
- **MASK**:  Mute Mask. The 4 lower bits represent the 4 audio channels.  
  
| `MASK`   | Channel 1 | Channel 2 | Channel 3 | Channel 4 |  
| -------- | --------- | --------- | --------- | --------- |  
| `0b0000` | Muted     | Muted     | Muted     | Muted     |  
| `0b0001` | Muted     | Muted     | Muted     | Not Muted |  
| `0b0010` | Muted     | Muted     | Not Muted | Muted     |  
| `0b0011` | Muted     | Muted     | Not Muted | Not Muted |  
| `0b0100` | Muted     | Not Muted | Muted     | Muted     |  
| `0b0101` | Muted     | Not Muted | Muted     | Not Muted |  
| `0b0110` | Muted     | Not Muted | Not Muted | Muted     |  
| `0b0111` | Muted     | Not Muted | Not Muted | Not Muted |  
| `0b1000` | Not Muted | Muted     | Muted     | Muted     |  
| `0b1001` | Not Muted | Muted     | Muted     | Not Muted |  
| `0b1010` | Not Muted | Muted     | Not Muted | Muted     |  
| `0b1011` | Not Muted | Muted     | Not Muted | Not Muted |  
| `0b1100` | Not Muted | Not Muted | Muted     | Muted     |  
| `0b1101` | Not Muted | Not Muted | Muted     | Not Muted |  
| `0b1110` | Not Muted | Not Muted | Not Muted | Muted     |  
| `0b1111` | Not Muted | Not Muted | Not Muted | Not Muted |  

### VM_SOUND_MASTERVOL

```gbvm
VM_SOUND_MASTERVOL VOL
```
 Sets master volume  
- **VOL**:  The volume value  

### VM_MUSIC_ROUTINE

```gbvm
VM_MUSIC_ROUTINE ROUTINE, BANK, ADDR
```
 Attach script to music event  
- **ROUTINE**:  The routine Id. An integer between 0 and 3.  
- **BANK**:  Bank number of the routine  
- **ADDR**:  Address of the routine  

### VM_SFX_PLAY

```gbvm
VM_SFX_PLAY BANK, ADDR, MASK, PRIO
```
 Play a sound effect asset  
- **BANK**:  Bank number of the effect  
- **ADDR**:  Address of the effect  
- **MASK**:  Mute mask of the effect  
- **PRIO**:  Priority of the sound effect. Effects with higher priority will cancel the ones with less priority:  
`.SFX_PRIORITY_MINIMAL` - Minmium priority for playback  
`.SFX_PRIORITY_NORMAL`  - Normal priority for playback0  
`.SFX_PRIORITY_HIGH`    - High priority for playback  

### VM_MUSIC_SETPOS

```gbvm
VM_MUSIC_SETPOS PATTERN, ROW
```
 Sets playback position for the current song.  
- **PATTERN**:     - The pattern to set the song position to  
- **ROW**:         - The row to set the song position to  

## Projectiles

### VM_PROJECTILE_LAUNCH

```gbvm
VM_PROJECTILE_LAUNCH TYPE, IDX
```
### VM_PROJECTILE_LOAD_TYPE

```gbvm
VM_PROJECTILE_LOAD_TYPE TYPE, BANK, ADDR
```
## RTC

### VM_RTC_LATCH

```gbvm
VM_RTC_LATCH
```
 Latch RTC value for access  

### VM_RTC_GET

```gbvm
VM_RTC_GET IDX, WHAT
```
 Read RTC value  
- **IDX**:  Target variable  
- **WHAT**:  RTC value to be read  
`.RTC_SECONDS` - Seconds  
`.RTC_MINUTES` - Minutes  
`.RTC_HOURS`   - Hours  
`.RTC_DAYS`    - Days  

### VM_RTC_SET

```gbvm
VM_RTC_SET IDX, WHAT
```
 Write RTC value  
- **IDX**:  Source variable  
- **WHAT**:  RTC value to be written  
`.RTC_SECONDS` - Seconds  
`.RTC_MINUTES` - Minutes  
`.RTC_HOURS`   - Hours  
`.RTC_DAYS`    - Days  

### VM_RTC_START

```gbvm
VM_RTC_START START
```
 Start or stop RTC  
- **START**:  Start or stop flag  
`.RTC_STOP`    - stop RTC  
`.RTC_START`   - start RTC  

## Rumble

### VM_RUMBLE

```gbvm
VM_RUMBLE ENABLE
```
 Enables or disables rumble on a cart that has that function  
- **ENABLE**:  1 - enable or 0 - disable  

## Scenes

### VM_SCENE_PUSH

```gbvm
VM_SCENE_PUSH
```
 Pushes the current scene to the scene stack.  

### VM_SCENE_POP

```gbvm
VM_SCENE_POP
```
 Removes the last scene from the scene stack an loads it.  

### VM_SCENE_POP_ALL

```gbvm
VM_SCENE_POP_ALL
```
 Removes all scenes from the scene stack and loads the first one.  

### VM_SCENE_STACK_RESET

```gbvm
VM_SCENE_STACK_RESET
```
 Removes all the scenes from the scene stack.  

## Screen Fade

### VM_FADE

```gbvm
VM_FADE FLAGS
```
### VM_FADE_IN

```gbvm
VM_FADE_IN IS_MODAL
```
### VM_FADE_OUT

```gbvm
VM_FADE_OUT IS_MODAL
```
## SGB

### VM_SGB_TRANSFER

```gbvm
VM_SGB_TRANSFER
```
 Transfers SGB packet(s). Data of variable length is placed after this instruction, for example:  
  
```  
VM_SGB_TRANSFER  
.db ((0x04 &lt;&lt; 3) | 1), 1, 0x07, ((0x01 &lt;&lt; 4) | (0x02 &lt;&lt; 2) | 0x03), 5,5, 10,10,  0, 0, 0, 0, 0, 0, 0, 0 ; ATTR_BLK packet  
```  
  
SGB packet size is a multiple of 16 bytes and encoded in the packet itself.  

## SIO

### VM_SIO_SET_MODE

```gbvm
VM_SIO_SET_MODE MODE
```
### VM_SIO_EXCHANGE

```gbvm
VM_SIO_EXCHANGE SOUR, DEST, SIZE
```
## Text Sound

### VM_SET_TEXT_SOUND

```gbvm
VM_SET_TEXT_SOUND BANK, ADDR, MASK
```
 Set the sound effect for the text output  
- **BANK**:  Bank number of the effect  
- **ADDR**:  Address of the effect  
- **MASK**:  Mute mask of the effect  

## Timer

### VM_TIMER_PREPARE

```gbvm
VM_TIMER_PREPARE TIMER, BANK, ADDR
```
Load script into timer context  

### VM_TIMER_SET

```gbvm
VM_TIMER_SET TIMER, INTERVAL
```
Start a timer calling once every `INTERVAL` * 16 frames  

### VM_TIMER_STOP

```gbvm
VM_TIMER_STOP TIMER
```
Stop a timer  

### VM_TIMER_RESET

```gbvm
VM_TIMER_RESET TIMER
```
Reset a timers countdown to 0  

## UI

### VM_LOAD_TEXT

```gbvm
VM_LOAD_TEXT NARGS
```
 Loads a text in memory  
- **NARGS**:  Amount of arguments that are passed before the null-terminated string  
  
The text string is defined using the `.asciz` command:  
  
```  
VM_LOAD_TEXT   0  
.asciz "text to render"  
```  
  
#### Displaying variables:  
The following format specifiers allow to render variables as part of the text:  
* `%d`  Render a variable value  
* `%Dn` Render a variable value with `n` length  
* `%c`  Render a character based on the variable value  
The variables need to be defined before the `.asciz` call using `.dw` followed by a list of `N` variables in the order they'll be rendered.  
```  
VM_LOAD_TEXT   3  
.dw VAR_0, VAR_1, VAR_1  
.asciz "Var 0 is %d, Var 1 is %d, Var 2 is %d"  
```  
#### Escape Sequences:  
The text string can contain escape sequence that modify the behavior or apparence of the text.  
* `\001\x` Sets the text speed for the next characters in the current text. `x` is a value between `1` and `8` that represents the number of frames between the render of a character using `2^(x-2)`.  
* `\002\x` Sets the text font  
* `\003\x\y` Sets the position for the next character  
* `\004\x\y` Sets the position for the next character relative to the last character  
* `\005\` TBD  
* `\006\mask` Wait for input to continue to the next character.  
* `\007\n` Inverts the colors of the following characters.  
* `\n` Next line  
* `\r` Scroll text one line up  

### VM_DISPLAY_TEXT_EX

```gbvm
VM_DISPLAY_TEXT_EX OPTIONS, START_TILE
```
 Renders the text in the defined layer (overlay, by default)  
- **OPTIONS**:  Text rendering options:  
`.DISPLAY_DEFAULT`      - default behavior  
`.DISPLAY_PRESERVE_POS` - preserve text position  
- **START_TILE**:  Tile number within the text rendering area to be rendered from; use .TEXT_TILE_CONTINUE to proceed from the current position  

### VM_DISPLAY_TEXT

```gbvm
VM_DISPLAY_TEXT
```
 Renders the text in the defined layer (obsolete)  

### VM_SWITCH_TEXT_LAYER

```gbvm
VM_SWITCH_TEXT_LAYER LAYER
```
 Changes the `LAYER` where the text will be rendered.  
- **LAYER**:   
`.TEXT_LAYER_BKG`    - Render text in the background layer  
`.TEXT_LAYER_WIN`    - Render text in the overlay layer  

### VM_OVERLAY_SETPOS

```gbvm
VM_OVERLAY_SETPOS X, Y
```
 Set position of the overlay window in tiles  
- **X**:  X-coordinate of the overlay window in tiles  
- **Y**:  Y-coordinate of the overlay window in tiles  

### VM_OVERLAY_HIDE

```gbvm
VM_OVERLAY_HIDE
```
 Hide the overlay window  

### VM_OVERLAY_WAIT

```gbvm
VM_OVERLAY_WAIT IS_MODAL, WAIT_FLAGS
```
 Wait for the UI operation(s) completion  
- **IS_MODAL**:  indicates whether the operation is modal: .UI_MODAL, or not: .UI_NONMODAL  
- **WAIT_FLAGS**:  bit field, set of events to be waited for:  
`.UI_WAIT_NONE`     - No wait  
`.UI_WAIT_WINDOW`   - Wait until the window moved to its final position  
`.UI_WAIT_TEXT`     - Wait until all the text finished rendering  
`.UI_WAIT_BTN_A`    - Wait until "A" is pressed  
`.UI_WAIT_BTN_B`    - Wait until "B" is pressed  
`.UI_WAIT_BTN_ANY`  - Wait until any button is pressed  

### VM_OVERLAY_MOVE_TO

```gbvm
VM_OVERLAY_MOVE_TO X, Y, SPEED
```
 Animated move of the overlay window to the new position  
- **X**:  X-coordinate of the new position  
- **Y**:  Y-coordinate of the new position  
- **SPEED**:  speed of the movement:  
`.OVERLAY_IN_SPEED`       - default speed for appearing of the overlay  
`.OVERLAY_OUT_SPEED`      - default speed for disappearing of the overlay  
`.OVERLAY_SPEED_INSTANT`  - instant movement  

### VM_OVERLAY_SHOW

```gbvm
VM_OVERLAY_SHOW X, Y, COLOR, OPTIONS
```
 Show the overlay window  
- **X**:  X-coordinate of the new position  
- **Y**:  Y-coordinate of the new position  
- **COLOR**:  initial color of the overlay window:  
`.UI_COLOR_BLACK`     - black overlay window  
`.UI_COLOR_WHITE`     - white overlay window  
- **OPTIONS**:  display options:  
`.UI_DRAW_FRAME`      - draw overlay frame  
`.UI_AUTO_SCROLL`     - set automatic text scroll area; text will be scrolled up when printing more lines than the overlay height.  

### VM_OVERLAY_CLEAR

```gbvm
VM_OVERLAY_CLEAR X, Y, W, H, COLOR, OPTIONS
```
 Clear the rectangle area of the overlay window  
- **X**:  X-coordinate in tiles of the upper left corner  
- **Y**:  Y-coordinate in tiles of the upper left corner  
- **W**:  Width in tiles of the rectangle area  
- **H**:  Height in tiles of the rectangle area  
- **COLOR**:  initial color of the overlay window:  
`.UI_COLOR_BLACK`     - black overlay window  
`.UI_COLOR_WHITE`     - white overlay window  
- **OPTIONS**:  display options:  
`.UI_DRAW_FRAME`      - draw overlay frame  
`.UI_AUTO_SCROLL`     - set automatic text scroll area; text will be scrolled up when printing more lines than the overlay height.  

### .MENUITEM

```gbvm
.MENUITEM X, Y, iL, iR, iU, iD
```
### VM_CHOICE

```gbvm
VM_CHOICE IDX, OPTIONS, COUNT
```
 Execute menu  
- **IDX**:  Variable that receive the result of the menu execution  
- **OPTIONS**:  bit field, set of the possible menu options:  
`.UI_MENU_STANDARD`    - default menu behavior  
`.UI_MENU_LAST_0`      - last item return result of 0  
`.UI_MENU_CANCEL_B`    - B button cancels the menu execution  
`.UI_MENU_SET_START`   - if set IDX may contain the initial item index  
- **COUNT**:  number of menu items  
  
instruction must be followed by the COUNT of .MENUITEM definitions:  
.MENUITEM X, Y, iL, iR, iU, iD  
where:  
`X` - X-coordinate of the cursor pointer in tiles  
`Y` - Y-coordinate of the cursor pointer in tiles  
`iL` - menu item number where the cursor must move when you press LEFT  
`iR` - menu item number where the cursor must move when you press RIGHT  
`iU` - menu item number where the cursor must move when you press UP  
`iD` - menu item number where the cursor must move when you press DOWN  

### VM_SET_FONT

```gbvm
VM_SET_FONT FONT_INDEX
```
 Sets active font  
- **FONT_INDEX**:  the index of the font to be activated  

### VM_SET_PRINT_DIR

```gbvm
VM_SET_PRINT_DIR DIRECTION
```
 Sets print direction  
- **DIRECTION**:  direction of the text rendering:  
`.UI_PRINT_LEFTTORIGHT`  - text is rendered from left to right (left justify)  
`.UI_PRINT_RIGHTTOLEFT`  - text is rendered from right to left (right justify)  

### VM_OVERLAY_SET_SUBMAP_EX

```gbvm
VM_OVERLAY_SET_SUBMAP_EX PARAMS_IDX
```
 Copies rectange area of the background map onto the overlay window  
- **PARAMS_IDX**:  points to the beginning of the pseudo-structure that contains these members:  
`x`       - X-coordinate within the overlay window in tiles  
`y`       - Y-coordinate tithin the overlay window in tiles  
`w`       - Width of the copied area in tiles  
`h`       - Height of the copied area in tiles  
`scene_x` - X-Coordinate within the background map in tiles  
`scene_y` - Y-Coordinate within the background map in tiles  

### VM_OVERLAY_SCROLL

```gbvm
VM_OVERLAY_SCROLL X, Y, W, H, COLOR
```
 Scrolls the rectangle area  
- **X**:  X-coordinate of the upper left corner in tiles  
- **Y**:  Y-coordinate of the upper left corner in tiles  
- **W**:  Width of the area in tiles  
- **H**:  Height of the area in tiles  
- **COLOR**:  Color of the empty row of tiles that appear at the bottom of the scroll area  

### VM_OVERLAY_SET_SCROLL

```gbvm
VM_OVERLAY_SET_SCROLL X, Y, W, H, COLOR
```
 Defines the scroll area for the overlay. When the text overflows that area it'll scroll up by 1 row  
- **X**:  X-coordinate of the upper left corner in tiles  
- **Y**:  Y-coordinate of the upper left corner in tiles  
- **W**:  Width of the area in tiles  
- **H**:  Height of the area in tiles  
- **COLOR**:  Color of the empty row of tiles that appear at the bottom of the scroll area  

### VM_OVERLAY_SET_SUBMAP

```gbvm
VM_OVERLAY_SET_SUBMAP X, Y, W, H, SX, SY
```
 Copies a rectange area of tiles from the scene background  
- **X**:  X-coordinate within the overlay window of the upper left corner in tiles  
- **Y**:  Y-coordinate within the overlay window of the upper left corner in tiles  
- **W**:  Width of the area in tiles  
- **H**:  Height of the area in tiles  
- **SX**:  X-coordinate within the level background map  
- **SY**:  Y-coordinate within the level background map  
