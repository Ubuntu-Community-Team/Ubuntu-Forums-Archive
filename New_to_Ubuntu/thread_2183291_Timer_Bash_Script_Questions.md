---
title: "Timer Bash Script Questions"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-10-24
I have found the following script online for a simple timer script:

```

#!/usr/bin/wish -f
    set intime [lindex $argv 0]
    set intimeI [expr $intime * 60]    

      proc countdown {seconds} {
          init
          countdown_kernel $seconds
      }
      
      
      proc countdown_kernel seconds {
          hands $seconds
          if !$seconds return
          after 1000
[list countdown_kernel [incr seconds -1]]
      }
      
      
      proc draw_hand {angle decorations} {
          eval .c create line $::size $::size [get_xy $angle] $decorations
      }
      
      
      proc end_coordinate difference {
          set hand_length [expr $::size * .9]
          return [expr $::size + $hand_length * $difference]
      }
      
      
      proc get_xy angle {
          return
[list [end_coordinate [expr sin($angle)]] \
                       [end_coordinate [expr -cos($angle)]]]
      }
      
      
      proc hands seconds {
          catch {.c delete withtag hands}
      
          set twopi 6.283185
          set seconds_angle [expr $seconds * $twopi / 60.]
          draw_hand $seconds_angle "-width 1 -tags hands"
          set minutes_angle [expr $seconds_angle / 60.]
          draw_hand $minutes_angle \
                       "-width 3 -capstyle projecting -tags hands"
      }
      
      proc init {} {
          catch {destroy .c}
          set ::size 90
          set full_diameter [expr 2 * $::size]
          pack [canvas .c -width $full_diameter -height $full_diameter]
          set border 2
          set diameter [expr 2 * $::size - $border]
          .c create oval $border $border \
                         $diameter $diameter \
                         -fill darkred -outline gold  
      }

      proc helw {} {
              wm title . "TIME IS UP!"
               button .bHello -text "Times Up!" -command exit
               pack .bHello
               exec play ~/sounds/doh.wav &
       }
      
      
      countdown $intimeI 
    after [expr $intimeI * 1000]  helw   

    

#      puts stdout "Time is $intimeI"

```

Questions:
a. I have just called it "Timer" I have chmod the script:
```

glenn@design:~/Desktop$ sudo chmod 775 Timer
glenn@design:~/Desktop$ ls -al Timer
-rwxrwxr-x 1 glenn glenn 1941 Oct 25 02:15 Timer
glenn@design:~/Desktop$

```
Is that correct?

b. How do I change the timer to run in seconds rather than minutes?
c. When I try to run the script, I get the following error:
```

glenn@design:~/Desktop$ sh Timer
Timer: 5: Timer: proc: not found
init: Need to be root
Timer: 7: Timer: countdown_kernel: not found
Timer: 8: Timer: Syntax error: "}" unexpected
glenn@design:~/Desktop$ 

```
I do't want to run the script as root.

Can someone please help.

---

### Post by Habitual on 2013-10-24
Simple non-root bash countdown timer:
```
MIN=1 && for i in $(seq $(($MIN*60)) -1 1); do echo -en "Launch in $i \r"; sleep 1; done; echo -e "nnMessage"
```

Hope that helps. :)

---

### Post by steeldriver on 2013-10-24
if it's a **wish **script (as indicated by the first line **#!/usr/bin/wish**) don't run it with **sh **- that's why you're getting the 'run as root' error message, the dash shell thinks you're trying to execute the SYSTEM init function instead of the Tcl init in the script - just invoke it as

```
./Timer
```

in the directory where it's located

---

### Post by Senior_Buckethead on 2013-10-24
Ok, I changed the /wish -f so the system didn't think it was a function call, and changed the first line to #!/bin/bash and renamed the file Timer2.

When I run it, I get:

```

glenn@design:~/Desktop$ ./Timer2
./Timer2: line 5: proc: command not found
init: Need to be root
./Timer2: line 7: countdown_kernel: command not found
./Timer2: line 8: syntax error near unexpected token `}'
./Timer2: line 8: `      }'
glenn@design:~/Desktop$ 

```

Does the 'proc' mean the script is trying to initiate a system function (guessing here) that it doesn't have permission to run? And has the removal of '/wish -f' removed that permission, or just made it so the system doesn't understand what follows, such as the errors below?

---

### Post by steeldriver on 2013-10-24
It is not a bash script - it's a wish script (a completely different language) --> [http://www.tcl.tk/man/tcl8.5/UserCmd/wish.htm](http://www.tcl.tk/man/tcl8.5/UserCmd/wish.htm)

You can't just magic it into a bash script by changing the shebang

---

### Post by Senior_Buckethead on 2013-10-24
If only it was all that easy. I've never heard of wish before. Thanks for the link. 
Easy to fix, just delete Timer 2 and use Timer again.

Question. Whe I created Timer2 with #!/bin/bash, the icon on the desktop (where I have the file, changed into, whatever you call it, a bin file, or whatever. The Timer2 file just looks like a normal file. Even though I have chmod it to 775

-rwxrwxr-x   1 glenn glenn      1941 Oct 25 04:34 Timer

Shouldn't it have the same icon as the Timer2 file had? 

When I run ./Timer, I get:

```

glenn@design:~/Desktop$ ./Timer
Error in startup script: missing operand at _@_
in expression "_@_* 60"
    (parsing expression "* 60")
    invoked from within
"expr $intime * 60"
    invoked from within
"set intimeI [expr $intime * 60]	"
    (file "./Timer" line 3)
glenn@design:~/Desktop$ 

```

---

### Post by Senior_Buckethead on 2013-10-24
Ahhh, its a ***Windowing Shell***. Alright, it makes a bit of sense now. SO all those procs are to draw things on the screen and start a system timer to make them all move right.

And of course, it *would be*, with those instructions on hands and stuff. duh.

---

