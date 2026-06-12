---
title: "general ncurses question"
date: 2009-10-09
forum: Programming Talk
---

### Post by openfly on 2009-10-09
I have an application that's running curses on a weird linux environment... a lot of the base paths of stuff are non standard.

I've set TERMINFO_DIRS and gotten the ncurses application to run.

BUT!

It goes to segmentation fault whenever I attempt to print string text to a window.

I thought it was a LOCALE issue, but I've been unable to make it work toggling environment vars.

ANY advice at all would be helpful.

---

### Post by openfly on 2009-10-09
Seeing this in strace:

```

11748 access("/opt/opsware/ogfsutils/share/terminfo/x/xterm", R_OK) = 0
11748 open("/opt/opsware/ogfsutils/share/terminfo/x/xterm", O_RDONLY) = 3
11748 read(3, "\32\0010\0&\0\17\0\235\1&\5", 12) = 12
11748 read(3, "xterm|xterm terminal emulator (X"..., 48) = 48
11748 read(3, "\0\1\0\0\1\0\0\0\1\0\0\0\0\1\1\0\0\0\0\0\0\0\1\0\0\1\0\0\1\0\0\0"..., 38) = 38
11748 read(3, "P\0\10\0\30\0\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\10\0@\0", 30) = 30
11748 read(3, "\0\0\4\0\6\0\10\0\31\0\36\0&\0*\0.\0\377\3779\0J\0L\0P\0W\0\377\377"..., 826) = 826
11748 read(3, "\33[Z\0\7\0\r\0\33[%i%p1%d;%p2%dr\0\33[3g\0\33["..., 1318) = 1318
11748 read(3, "\1\0\0\0\v\0\27\0\200\0", 10) = 10
11748 read(3, "\1", 1)                  = 1
11748 read(3, "\0", 1)                  = 1
11748 read(3, "\377\377\0\0\7\0\16\0\25\0\34\0#\0*\0001\0008\0?\0\0\0\3\0\6\0\n\0\17\0"..., 46) = 46
11748 read(3, "\33[1;2B\0\33[1;5B\0\33[1;6B\0\33[1;5D\0\33[1;"..., 128) = 128
11748 close(3)                          = 0
11748 ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, TIOCGWINSZ, {ws_row=69, ws_col=170, ws_xpixel=0, ws_ypixel=0}) = 0
11748 ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, SNDCTL_TMR_STOP or TCSETSW, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, SNDCTL_TMR_STOP or TCSETSW, {B38400 opost isig -icanon -echo ...}) = 0
11748 rt_sigaction(SIGTSTP, NULL, {SIG_DFL}, 8) = 0
11748 rt_sigaction(SIGTSTP, {0x2a98caef30, [], SA_RESTORER|SA_RESTART, 0x2a9577b5b0}, NULL, 8) = 0
11748 rt_sigaction(SIGINT, NULL, {SIG_IGN}, 8) = 0
11748 rt_sigaction(SIGTERM, NULL, {SIG_IGN}, 8) = 0
11748 rt_sigaction(SIGWINCH, NULL, {SIG_DFL}, 8) = 0
11748 rt_sigaction(SIGWINCH, {0x2a98caf1d0, [], SA_RESTORER, 0x2a9577b5b0}, NULL, 8) = 0
11748 ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, SNDCTL_TMR_STOP or TCSETSW, {B38400 opost isig -icanon -echo ...}) = 0
11748 write(1, "\33[?1049h\33[1;69r\33(B\33[m\33[4l\33[?7h\33["..., 37) = 37
11748 rt_sigaction(SIGTSTP, {SIG_IGN}, {0x2a98caef30, [], SA_RESTORER|SA_RESTART, 0x2a9577b5b0}, 8) = 0
11748 ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig -icanon -echo ...}) = 0
11748 ioctl(1, TIOCGWINSZ, {ws_row=69, ws_col=170, ws_xpixel=0, ws_ypixel=0}) = 0
11748 write(1, "\33[H\33[2J\33(0\33[0mlqqqqqqqqqqqqqqqqq"..., 927) = 927
11748 rt_sigaction(SIGTSTP, {0x2a98caef30, [], SA_RESTORER|SA_RESTART, 0x2a9577b5b0}, NULL, 8) = 0
11748 --- SIGSEGV (Segmentation fault) @ 0 (0) ---
11748 +++ killed by SIGSEGV +++

```

I am baffled.

---

### Post by wmcbrine on 2009-10-09
It might help if we could see your source.

---

### Post by openfly on 2009-10-13
It won't.  It's definitely an environment issue.

---

