---
title: "What did I do?"
date: 2011-12-02
forum: Programming Talk
---

### Post by Saroset on 2011-12-02
This:
```
section .text
	global _start	;

_start:
	pop ebx
	pop ebx
	pop ebx
	mov ecx, ebx	;move to c
	mov eax, 4	;write
	mov ebx, 1	;std_out
	mov edx, 500
	int 0x80
	mov eax, 1
	mov ebx, 0
	int 0x80
```

Produced this:

```
SSH_AGENT_PID=1808GPG_AGENT_INFO=/tmp/keyring-0PiQa4/gpg:0:1TERM=xtermSHELL=/bin/bashXDG_SESSION_COOKIE=9baab90259df3a8448ba027900000007-1322553645.771334-780363822WINDOWID=44040198GNOME_KEYRING_CONTROL=/tmp/keyring-0PiQa4GTK_MODULES=canberra-gtk-module:canberra-gtk-moduleUSER=alexLS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj
```

Any idea what I drug out?

---

### Post by Bachstelze on 2011-12-02
The environment of your process. Not any Top Secret stuff, sorry. ;)

---

### Post by SevenMachines on 2011-12-02
Hopefully this is fairly well remembered by me from a while back :), just so you can see where this all comes from

The stack as linux launches a command looks something like this, with the stack pointer at the 'top' of the stack as shown, and various bits and pieces on the stack as shown.

==================
Null Pointer
Executable Path
Actual Environment Variables
Actual Args
System Things
Null Pointer
Address of Environment Variable ...
Address of Environment Variable 2
Address of Environment Variable 1
Null Pointer
Address of Arg2
Address of Arg1
Address of Executable Text
Argument Count                     <---ESP
==================

Using a simple hello world program and gdb shows the initial stack frame a bit more practically

```
$ gdb -q ./hello
Reading symbols from /home/seven/Desktop/hello...done.
```#Break directly at entry point
```

(gdb) break _start
Breakpoint 1 at 0x8048320
```# Then run with 2 arguments to demonstrate stack layout
```

(gdb) run A B
Starting program: /home/seven/Desktop/hello A B

Breakpoint 1, 0x08048320 in _start ()
```# Now lets look at 64 w(ords) in (he)x starting at the stack pointer
```

((gdb) x /64uwx $esp
0xffffd100:    0x00000003    0xffffd2b3    0xffffd2cd    0xffffd2cf
0xffffd110:    0x00000000    0xffffd2d1    0xffffd2ea    0xffffd31e
0xffffd120:    0xffffd331    0xffffd35c    0xffffd36c    0xffffd377
0xffffd130:    0xffffd3c7    0xffffd3d9    0xffffd403    0xffffd429
0xffffd140:    0xffffd45d    0xffffd466    0xffffd471    0xffffd961
0xffffd150:    0xffffd984    0xffffd9be    0xffffd9f2    0xffffda18
0xffffd160:    0xffffda6d    0xffffdaa0    0xffffdaaf    0xffffdb0b
0xffffd170:    0xffffdb17    0xffffdb44    0xffffdb5b    0xffffdc3a
0xffffd180:    0xffffdc52    0xffffdc61    0xffffdc78    0xffffdc90
0xffffd190:    0xffffdc9b    0xffffdcac    0xffffdcc3    0xffffdce0
0xffffd1a0:    0xffffdd16    0xffffdd33    0xffffdd52    0xffffdd5b
0xffffd1b0:    0xffffdd6d    0xffffdd7e    0xffffdd86    0xffffdd98
0xffffd1c0:    0xffffddc4    0xffffdddc    0xffffddea    0xffffddff
0xffffd1d0:    0xffffde61    0xffffdeb0    0xffffded0    0xffffdeea
0xffffd1e0:    0xffffdf59    0xffffdf66    0xffffdf80    0xffffdfa2
0xffffd1f0:    0xffffdfc5    0x00000000    0x00000020    0xf7fdd420
```# At esp we have the number of arguments, 3 (0x00000003) (which is true since we're being passed not just the 2 actual args but also the text of the program call too as a 'hidden' arg), then the executable text address  + then the 2 argument addresses

# The executable text
```

(gdb) x/s 0xffffd2b3
0xffffd2b3:     "/home/seven/Desktop/hello"
```# And the 2 arguments
```

(gdb) x/s 0xffffd2cd
0xffffd2cd:     "A"
(gdb) x/s 0xffffd2cf
0xffffd2cf:     "B"
```# Then we have a null pointer 0x00000000 followed by all our environment variables before another 0x00000000
```

(gdb) x/s 0xffffd2d1
0xffffd2d1:     "LIBOVERLAY_SCROLLBAR=foo"
(gdb) x/s 0xffffd2ea
0xffffd2ea:     "QUILT_REFRESH_ARGS=-p ab --no-timestamps --no-index"
(gdb) x/s 0xffffdfc5
0xffffdfc5:     "COLORTERM=gnome-terminal" 
```Hopefully that sort of helps make sense of your assembly, what you're popping off the stack with 'pop ebx', and so at which point in the stack you're writing a chunk out.

---

