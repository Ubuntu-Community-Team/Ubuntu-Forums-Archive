---
title: "weird linker error with allegro"
date: 2011-10-30
forum: Packaging and Compiling Programs
---

### Post by orenwatson on 2011-10-30
I just upgraded to 11.10, and my program no longer compiles due to a linker error. My compile command is:
```
gcc -L/usr/local/lib -lalleg -Wall -Wextra -o rktboytris rktboytris.c
```
It gives me the following errors:
```
rktboytris.c: In function ‘draw_block_back’:
rktboytris.c:313:26: warning: unused parameter ‘f’ [-Wunused-parameter]
/tmp/ccdqUR0M.o: In function `vline':
rktboytris.c:(.text+0x29): undefined reference to `_allegro_vline'
/tmp/ccdqUR0M.o: In function `hline':
rktboytris.c:(.text+0x58): undefined reference to `_allegro_hline'
/tmp/ccdqUR0M.o: In function `input_box':
rktboytris.c:(.text+0xe9): undefined reference to `clear_keybuf'
rktboytris.c:(.text+0x144): undefined reference to `keypressed'
rktboytris.c:(.text+0x151): undefined reference to `readkey'
rktboytris.c:(.text+0x25d): undefined reference to `screen'
rktboytris.c:(.text+0x265): undefined reference to `screen'
rktboytris.c:(.text+0x26d): undefined reference to `screen'
rktboytris.c:(.text+0x2a6): undefined reference to `blit'
rktboytris.c:(.text+0x2b1): undefined reference to `screen'
rktboytris.c:(.text+0x2ee): undefined reference to `textprintf_right_ex'
rktboytris.c:(.text+0x2f9): undefined reference to `screen'
rktboytris.c:(.text+0x336): undefined reference to `textprintf_ex'
rktboytris.c:(.text+0x3b6): undefined reference to `text_length'
rktboytris.c:(.text+0x3c0): undefined reference to `screen'
/tmp/ccdqUR0M.o: In function `draw_block_back':
rktboytris.c:(.text+0x12fb): undefined reference to `rect'
/tmp/ccdqUR0M.o: In function `draw_block_side':
rktboytris.c:(.text+0x1417): undefined reference to `polygon'
rktboytris.c:(.text+0x1476): undefined reference to `polygon'
rktboytris.c:(.text+0x14c9): undefined reference to `polygon'
rktboytris.c:(.text+0x151c): undefined reference to `polygon'
rktboytris.c:(.text+0x1551): undefined reference to `line'
rktboytris.c:(.text+0x1581): undefined reference to `line'
rktboytris.c:(.text+0x15b1): undefined reference to `line'
rktboytris.c:(.text+0x15e1): undefined reference to `line'
/tmp/ccdqUR0M.o: In function `draw_block_front':
rktboytris.c:(.text+0x1665): undefined reference to `rectfill'
rktboytris.c:(.text+0x1697): undefined reference to `rect'
/tmp/ccdqUR0M.o: In function `display':
rktboytris.c:(.text+0x1890): undefined reference to `clear_to_color'
rktboytris.c:(.text+0x1b98): undefined reference to `line'
rktboytris.c:(.text+0x1bc8): undefined reference to `line'
rktboytris.c:(.text+0x1bf8): undefined reference to `line'
rktboytris.c:(.text+0x1c28): undefined reference to `line'
rktboytris.c:(.text+0x1ceb): undefined reference to `line'
/tmp/ccdqUR0M.o:rktboytris.c:(.text+0x1d1b): more undefined references to `line' follow
/tmp/ccdqUR0M.o: In function `display':
rktboytris.c:(.text+0x23ce): undefined reference to `textprintf_ex'
rktboytris.c:(.text+0x2419): undefined reference to `textprintf_ex'
rktboytris.c:(.text+0x2464): undefined reference to `textprintf_ex'
rktboytris.c:(.text+0x24ad): undefined reference to `textprintf_ex'
rktboytris.c:(.text+0x24f8): undefined reference to `textprintf_ex'
rktboytris.c:(.text+0x24fd): undefined reference to `screen'
rktboytris.c:(.text+0x2505): undefined reference to `screen'
rktboytris.c:(.text+0x250d): undefined reference to `screen'
rktboytris.c:(.text+0x2546): undefined reference to `blit'
/tmp/ccdqUR0M.o: In function `gamepause':
rktboytris.c:(.text+0x3308): undefined reference to `clear_keybuf'
rktboytris.c:(.text+0x334f): undefined reference to `textprintf_centre_ex'
rktboytris.c:(.text+0x338f): undefined reference to `textprintf_centre_ex'
rktboytris.c:(.text+0x33c8): undefined reference to `rectfill'
rktboytris.c:(.text+0x3408): undefined reference to `textprintf_centre_ex'
rktboytris.c:(.text+0x349a): undefined reference to `textprintf_centre_ex'
rktboytris.c:(.text+0x34da): undefined reference to `textprintf_centre_ex'
rktboytris.c:(.text+0x351a): undefined reference to `textprintf_centre_ex'
rktboytris.c:(.text+0x3527): undefined reference to `voice_get_volume'
rktboytris.c:(.text+0x3574): undefined reference to `textprintf_centre_ex'
rktboytris.c:(.text+0x35e5): undefined reference to `textprintf_ex'
rktboytris.c:(.text+0x3649): undefined reference to `textprintf_right_ex'
rktboytris.c:(.text+0x366e): undefined reference to `keypressed'
rktboytris.c:(.text+0x3677): undefined reference to `readkey'
rktboytris.c:(.text+0x369d): undefined reference to `mouse_b'
rktboytris.c:(.text+0x36b3): undefined reference to `mouse_x'
rktboytris.c:(.text+0x36c6): undefined reference to `mouse_x'
rktboytris.c:(.text+0x36d3): undefined reference to `mouse_y'
rktboytris.c:(.text+0x36e3): undefined reference to `mouse_y'
rktboytris.c:(.text+0x36f3): undefined reference to `mouse_y'
rktboytris.c:(.text+0x370f): undefined reference to `mouse_y'
rktboytris.c:(.text+0x377d): undefined reference to `screen'
rktboytris.c:(.text+0x378d): undefined reference to `clear_to_color'
rktboytris.c:(.text+0x3797): undefined reference to `mouse_y'
rktboytris.c:(.text+0x380a): undefined reference to `mouse_y'
rktboytris.c:(.text+0x3822): undefined reference to `voice_get_volume'
rktboytris.c:(.text+0x3844): undefined reference to `voice_set_volume'
rktboytris.c:(.text+0x384e): undefined reference to `screen'
rktboytris.c:(.text+0x3856): undefined reference to `screen'
rktboytris.c:(.text+0x385e): undefined reference to `screen'
rktboytris.c:(.text+0x3897): undefined reference to `blit'
rktboytris.c:(.text+0x389d): undefined reference to `mouse_y'
rktboytris.c:(.text+0x38a3): undefined reference to `mouse_x'
rktboytris.c:(.text+0x38a8): undefined reference to `screen'
rktboytris.c:(.text+0x38c8): undefined reference to `circlefill'
rktboytris.c:(.text+0x38e0): undefined reference to `rest'
/tmp/ccdqUR0M.o: In function `game':
rktboytris.c:(.text+0x3918): undefined reference to `keypressed'
rktboytris.c:(.text+0x3925): undefined reference to `readkey'
/tmp/ccdqUR0M.o: In function `main':
rktboytris.c:(.text+0x4308): undefined reference to `_install_allegro_version_check'
rktboytris.c:(.text+0x4314): undefined reference to `set_color_depth'
rktboytris.c:(.text+0x4340): undefined reference to `set_gfx_mode'
rktboytris.c:(.text+0x435c): undefined reference to `load_font'
rktboytris.c:(.text+0x436c): undefined reference to `screen'
rktboytris.c:(.text+0x43a0): undefined reference to `textprintf_centre_ex'
rktboytris.c:(.text+0x43a5): undefined reference to `screen'
rktboytris.c:(.text+0x43ba): undefined reference to `install_keyboard'
rktboytris.c:(.text+0x43bf): undefined reference to `install_mouse'
rktboytris.c:(.text+0x43c4): undefined reference to `screen'
rktboytris.c:(.text+0x43cc): undefined reference to `screen'
rktboytris.c:(.text+0x43da): undefined reference to `create_bitmap'
rktboytris.c:(.text+0x456c): undefined reference to `install_timer'
rktboytris.c:(.text+0x4588): undefined reference to `install_sound'
rktboytris.c:(.text+0x459a): undefined reference to `allegro_error'
rktboytris.c:(.text+0x45c6): undefined reference to `create_sample'
rktboytris.c:(.text+0x46a1): undefined reference to `play_sample'
rktboytris.c:(.text+0x46bb): undefined reference to `install_int_ex'
rktboytris.c:(.text+0x46c8): undefined reference to `set_close_button_callback'
rktboytris.c:(.text+0x46dc): undefined reference to `set_keyboard_rate'
rktboytris.c:(.text+0x46e8): undefined reference to `simulate_keypress'
rktboytris.c:(.text+0x472d): undefined reference to `rest'
rktboytris.c:(.text+0x4734): undefined reference to `key'
collect2: ld returned 1 exit status
make: *** [rktboytris] Error 1
```
Which is garbage, because I KNOW that /usr/local/lib/liballeg.so contains those functions. I tested this with nm, for example "textprintf_centre_ex" is in it:
```
$ nm /usr/local/lib/liballeg.so | grep "textprintf_centre_ex"
000778a0 T textprintf_centre_ex
```
What could be causing this????:-x

---

### Post by MadCow108 on 2011-10-30
it must be 
```
gcc -L/usr/local/lib -Wall -Wextra -o rktboytris rktboytris.c -lalleg
```

see every other undefined ref thread in this forum for more info

---

### Post by SevenMachines on 2011-10-30
I think madcow108 deserves a medal for the amount of help he's given on the 'as-needed' change :)

---

### Post by orenwatson on 2011-10-30
How do I change it back to --no-as-needed by default?
I have many makefiles which use this assumption, I want this changed back, centrally.
EDIT: Ugh, this is so typical of Ubuntu nowadays "We know better than you, this is the right way, so interrupt your work and spend 3 hours changing stuff to the way we want it!" The bloody Unity thing was garbage, made me go to Xubuntu, but now you're even messing up my dev environment?!

---

