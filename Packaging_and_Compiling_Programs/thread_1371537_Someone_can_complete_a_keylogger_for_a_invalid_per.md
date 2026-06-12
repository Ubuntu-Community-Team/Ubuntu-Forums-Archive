---
title: "Someone can complete a keylogger for a invalid person?"
date: 2010-01-03
forum: Packaging and Compiling Programs
---

### Post by N!coz on 2010-01-03
Hi all!

In the ubuntu italian community some people create for me a keylogger.
Now i tell the problem, i'm installing a machine for a invalid person that use this keyboard : [http://www.bigkeys.com/productcart/pc/viewPrd.asp?idcategory=2&idproduct=2](http://www.bigkeys.com/productcart/pc/viewPrd.asp?idcategory=2&idproduct=2)

But i need a sound when key is pressed. In keyboard setup i can enable the
"slowdown keys" but this option is in contrast with another option activated.
Practically the only way is to create a program, pyton daemon , or a similar.
Someone have resolved my problem with a keylogger. I put an audio.waw files in the directory of the keylogger and when i start it ( sudo ./beep) i can hear the tones.
But the problem is one, this keylogger is created for a PS/2 keyboard, but the mine is USB  and i can't use the traditional adapter for swith to usb.
Someone can modify the keylogger to work with the usb?
I hope that my english is comprehensible, thanks in advance.
Best regards

---

### Post by Martje_001 on 2010-01-03
Hi N!coz,

When do you want to hear the beep? With **every** keypress? If yes: I could easily create something for you.

---

### Post by N!coz on 2010-01-03
> **Martje_001 said:**
> Hi N!coz,

When do you want to hear the beep? With **every** keypress? If yes: I could easily create something for you.

O_O i don't believe that you have a solutions! O_O
Yes , after the logging i want the beep when i push  every key indistinctly!

---

### Post by Martje_001 on 2010-01-03
1. Save the file attached to your home-folder.
2. Go to a terminal and type:
```
sudo python detectInput.py
```
3. Wait a few seconds
4. Press a random key on your keyboard (1 or 2 times)

Does it respond?

---

### Post by N!coz on 2010-01-03
> **Martje_001 said:**
> 1. Save the file attached to your home-folder.
2. Go to a terminal and type:
```
sudo python detectInput.py
```
3. Wait a few seconds
4. Press a random key on your keyboard (1 or 2 times)

Does it respond?

First of all i want to thanks you for you help and your avaibility..

I have followed your instruction , when in the terminal appear the line : platform-i8042-serio-0-event-kdb   i try to press the key on keyboard but i don't hear any sound!

I must tell you that i'm trying on a laptop , your program must be run on a normal keyboard system ps/2 ? is here the problem?

---

### Post by Martje_001 on 2010-01-04
Hi N!coz,

The output is absolutely fine. This was a test whether your keyboard was detected like a normal keyboard or not. I turns out it is!

When I'm back at home (in 9 hours or so), I'll write a script which will play a sound with every keypress.

---

### Post by N!coz on 2010-01-04
> **Martje_001 said:**
> Hi N!coz,

The output is absolutely fine. This was a test whether your keyboard was detected like a normal keyboard or not. I turns out it is!

When I'm back at home (in 9 hours or so), I'll write a script which will play a sound with every keypress.

OH you are so kindly!
But i have a puntualization. I have tried your application on a laptop and on my pc desktop. I have do this for a testing, but i have not tried on the machine with the BIG KEYS keyboard. Is necessary trying also on the big keys lx keyboard? I answer that because this machine is not near to me!

---

### Post by Martje_001 on 2010-01-04
Yes, it is necessary to test this on the big-key keyboard ;). I've written another script for you (attached). Run it this way:

```
sudo python beep.py [keyboard] [sound]
```
[keyboard] == output of previous script
[audio] == Absolute path of sound file

So, for example:

```
sudo python beep.py platform-i8042-serio-0-event-kdb /home/ncoz/beep.wav
```

Does this work?

---

### Post by N!coz on 2010-01-04
> **Martje_001 said:**
> Yes, it is necessary to test this on the big-key keyboard ;). I've written another script for you (attached). Run it this way:

```
sudo python beep.py [keyboard] [sound]
```
[keyboard] == output of previous script
[audio] == Absolute path of sound file

So, for example:

```
sudo python beep.py platform-i8042-serio-0-event-kdb /home/ncoz/beep.wav
```

Does this work?


now i go to the machine and i try immediately! wait me

---

### Post by N!coz on 2010-01-04
Bad notice;

first of all i've launched the old program and i've annotated the code.

After i've put the wav files and the new pyton program in home folder and the result is this:

arturo@ubu-artur:~$ sudo python beep.py kpci-0000:00:03.1-usb-0:1:1.0-event-kbd /home/arturo/tast.wav
[sudo] password for arturo: 
Traceback (most recent call last):
  File "beep.py", line 4, in <module>
    f = open('/dev/input/by-path/%s' % sys.argv[1],'rb')
IOError: [Errno 2] No such file or directory: '/dev/input/by-path/kpci-0000:00:03.1-usb-0:1:1.0-event-kbd'
arturo@ubu-artur:~$ 

I'm so sad :(

---

### Post by realzippy on 2010-01-04
> **N!coz said:**
> Bad notice;

first of all i've launched the old program and i've annotated the code.

After i've put the wav files and the new pyton program in home folder and the result is this:

arturo@ubu-artur:~$ sudo python beep.py [COLOR="Red"]k[/COLOR]pci-0000:00:03.1-usb-0:1:1.0-event-kbd /home/arturo/tast.wav
[sudo] password for arturo: 
Traceback (most recent call last):
  File "beep.py", line 4, in <module>
    f = open('/dev/input/by-path/%s' % sys.argv[1],'rb')
IOError: [Errno 2] No such file or directory: '/dev/input/by-path/kpci-0000:00:03.1-usb-0:1:1.0-event-kbd'
arturo@ubu-artur:~$ 

I'm so sad :(

No need to. 
You typed a "k" when running first script (marked red)  ;-)
it is not part of the output.
Try again:

**sudo python beep.py pci-0000:00:03.1-usb-0:1:1.0-event-kbd /home/arturo/tast.wav**

Edit:
BTW,script works.
Maybe it should detect some applications and stop itself,otherwise some apps might be funny...editing text e.g.
Edit2:
Thanks to Martje!!It is fun also ;-) ..depending on wave-file...

---

### Post by Martje_001 on 2010-01-04
N!coz, Realzippy is correct. You probably ran the script and pressed the 'k'-key on your keyboard.

Run it again like Realzippy said ;). Let me know how it goes!

---

### Post by realzippy on 2010-01-04
Martje,with a timer or countdown it would be great for limiting kid's
computer time...some ugly *stopitnow.wav*

---

### Post by N!coz on 2010-01-04
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
IT WORKSSS
IT WORKKKSSS
IT WORKS FINEEEEEEEEEEEEE!! I CAN HEAR A BIIIP! !!!!!!!!!

Well now remain the latest problem, because the machine is used by a invalid person, i need that the script run without any command.

On the ubuntu italian forum community we have study some  way but at present, no one works. I summarize now :

first idea was to edit the "sudoers" with visudo.
At the bottom insert this line: %beepgroup    ALL=(root) NOPASSWD: /usr/bin/beep   ( i need to copy the file .py in that directory obviusly)
Create a beepgroup and put the user into that group, and in theory, when i launch by the console the pwd was not necessary. But this way don't work fine.

Another idea was to 
1: sudo chown root:root /directoryof.py
2: sudo chmod a+s /directoryof.py
3: try to write the command in " system -> starting application -> create a new one.

But probably i have do something wrong because it don't work !

---

### Post by N!coz on 2010-01-04
> **realzippy said:**
> Martje,with a timer or countdown it would be great for limiting kid's
computer time...some ugly *stopitnow.wav*

thanks realzippy for you help..

but i don't understand what do you intend. Can you write with another words please? my english is so bad :(

---

### Post by Martje_001 on 2010-01-04
Is he the only user on the system? If so, you could do something like this:

```
sudo cp beep.py /usr/bin/
sudo gedit /etc/init.d/beep
```
Paste the following (replace the [*] of course):
```
#!/bin/bash
python /usr/bin/beep.py [keyboard] [wavefile]
```
Save it, close it and:
```
sudo chmod +x /etc/init.d/beep
sudo update-rc.d beep defaults
```
I **think** that should work.

Edit: This will start "beep.py" everytime the computers starts.

---

### Post by realzippy on 2010-01-04
> **N!coz said:**
> thanks realzippy for you help..

but i don't understand what do you intend. Can you write with another words please? my english is so bad :(

,,,sorry,was offtopic.
Played around with this script and WAVs from [http://www.dooleydrums.com/](http://www.dooleydrums.com/)
and had the idea that it also could help to "*shrink young person's computer abuse*" by running a WAV "Stop it!" every keyboard input after given time...

---

### Post by N!coz on 2010-01-04
I have no words! All works!
But there is a new problem, when i turn off the machine, the monitor go in black colour and appear a line :

INIT: USPLASH post-start process (3960) Terminated with status 1

:(

---

### Post by N!coz on 2010-01-04
An italian power user tell me that probably there are some problems with the levels of updare-rc.d

He try to modify the script for use it with a setted runlevel eg. 
sudo update-rc.d beep start 2345 stop 016



```
#!/bin/bash
test -f beep || exit 0
case "$1" in
 start)
   echo -n "Avvio beep: beep"
   python /home/thebigbug/beep.py pci-0000:00:1d.2-usb-0:1.1:1.0-event-kbd /home/thebigbug/top.wav
   echo "."
   ;;
 stop)
   echo -n "Arresto beep: beep"
   kill `cat /var/run/beep.pid`
   echo "."
   ;;
 restart)
   echo -n "Arresto beep: beep"
   kill `cat /var/run/beep.pid`
   echo "."
   echo -n "Avvio beep: beep"
   python /home/thebigbug/beep.py pci-0000:00:1d.2-usb-0:1.1:1.0-event-kbd /home/thebigbug/top.wav
   echo "."
 *)
   echo "Uso: /etc/init.d/beep start|stop|restart"
   exit 1
   ;;
esac
```

But he tell me that in this script there are some problems..
1. when i type: sudo cat /var/run/*.pid    i receive some numbers 
eg. 1551
1406
1550
1885
2124
1527990
1579
606

to that number corresponding a process with a name.
If i know the name i can stop the started beep process.. But at this level we are not able to continue the work.. :(

---

### Post by realzippy on 2010-01-05
I do not understand what you want....
Stop the script?:

**killall python /path/to/your/scriptfolder/beep.py**

...you could create a "Starter" (Stopper) for this on the Desktop...

---

### Post by N!coz on 2010-01-05
> **realzippy said:**
> I do not understand what you want....
Stop the script?:

**killall python /path/to/your/scriptfolder/beep.py**

...you could create a "Starter" (Stopper) for this on the Desktop...

Now i explain you what i'm thinking.

This machine is used by a invalid person, when he log into his profile user, all the things must be activated!
Therefore the beep.py must be activated when he log in , in fact this function work well after the use of a script in /usr/bin and the use of init.d.
Now the problem is the messagge that appear when i turn off the machine, the machine don't arrest and is blocked on a black screen (such as the console environment) and the only message is :
Init: usplash post-start process (3960) Terminated with status 1 :popcorn:

---

### Post by realzippy on 2010-01-05
Please test:

**killall python /path/to/your/scriptfolder/beep.py**


before shutdown.
Does it work?

---

### Post by N!coz on 2010-01-05
> **realzippy said:**
> Please test:

**killall python /path/to/your/scriptfolder/beep.py**


before shutdown.
Does it work?


Sorry for the question but the folder that you mean is about script or beep.py? because my setup is :

sudo cp beep.py /usr/bin/   <- the place where is now beep.py
sudo gedit /etc/init.d/beep  <- the script that i have created 

then the right folder is  "killal python /etc/init.d/beep.py ? is correct? but in the folder of the script there is no file called beep.py!

---

### Post by realzippy on 2010-01-05
So it should be:

**sudo killall python /usr/bin/beep.py**

---

### Post by N!coz on 2010-01-05
> **realzippy said:**
> So it should be:

**sudo killall python /usr/bin/beep.py**

I'm returned now...
I've tested your instruction, when i digit che line the message is :

/usr/bin/beep.py :No process found

But the sound stop , i don't hear anything! But when i turn off the machine the problem remain the same :(

If there is no way to resolve this problem, let me tell the way to return to the standard situation ( before the use of update-rc.d) , and i try to create a launcher on the desktop. In this case i hope that the persone is able to doubleclick to activate the key sound ..:confused:

---

### Post by realzippy on 2010-01-05
Yes,return to standard (delete "beep",keep "beep.py")
beep.py can be started by adding to "sessions" in System/Settings/sessions  ..

---

### Post by N!coz on 2010-01-05
> **realzippy said:**
> Yes,return to standard (delete "beep",keep "beep.py")
beep.py can be started by adding to "sessions" in System/Settings/sessions  ..

and about the command update-rc.d ? when i delete the script in init.d this command don't create problem  , right?

When i add the session i put beep.py in home folder and i write in the space "command" , the folder of beep.py .

---

### Post by realzippy on 2010-01-05
sudo rm /etc/init.d/beep

should delete your beep in init.d.....

No,the command would be:

**python beep.py pci-0000:00:03.1-usb-0:1:1.0-event-kbd /home/arturo/tast.wav**

to make it work without sudo you have to chmod 755 your keyboard..

[B[COLOR="Red"]]sudo chmod 755 /dev/input/by-path/pci-0000:00:03.1-usb-0:1:1.0-event-kbd[/COLOR][/B]


[COLOR="Red"]
EDIT[/COLOR]: Just see that it works only after log out,after reboot it does not...wait.I will check this out.

---

### Post by N!coz on 2010-01-05
> **realzippy said:**
> sudo rm /etc/init.d/beep

should delete your beep in init.d.....

No,the command would be:

**python beep.py pci-0000:00:03.1-usb-0:1:1.0-event-kbd /home/arturo/tast.wav**

to make it work without sudo you have to chmod 755 your keyboard..

[B[COLOR="Red"]]sudo chmod 755 /dev/input/by-path/pci-0000:00:03.1-usb-0:1:1.0-event-kbd[/COLOR][/B]


[COLOR="Red"]
EDIT[/COLOR]: Just see that it works only after log out,after reboot it does not...wait.I will check this out.

I have do all the things that you have say..
And now it works.. i have immediately reboot ( not logout ) and all works... i have reboot many times for test this solution! I don't understand one things, why we have tried the other solution with init.d , script etc, when this one is so easy and fast to configure? ( just a personal question ;) )

---

### Post by Martje_001 on 2010-01-05
Because it's not safe! Anyone on your system could read your typed characters (including passwords!). Moreover, beeps won't work in the login screen. The correct solution would be to let **/usr/init.d/beep** save it's PID after it starts and when the system shuts down it would kill this PID.

[SIZE="1"]Some people suggest things without knowing what they'll do. Fools. :([/SIZE]

Anyway, I'm happy it's working for you now.

Edit: I see some other problems too.. but hey..

---

### Post by realzippy on 2010-01-05
> **Martje_001 said:**
> Because it's not safe! Anyone on your system could read your typed characters (including passwords!). Moreover, beeps won't work in the login screen. The correct solution would be to let **/usr/init.d/beep** save it's PID after it starts and when the system shuts down it would kill this PID.

[SIZE="1"]Some people suggest things without knowing what they'll do. Fools. :([/SIZE]

Anyway, I'm happy it's working for you now.

Edit: I see some other problems too.. but hey..

..I have to admit that I should have deleted it instead of marking it red.
Quick dirty solution I thought since I was not able to reproduce the shutdown error;also thought it was a single-user-system (Post #16).
So,if you have a solution for OP's error.....it would be highly recommended to prefer this.:)

---

### Post by Martje_001 on 2010-01-05
Realzippy: I didn't mean to offend you of course. If I did: I hereby apologize. It just that I sometimes get fed up with bad "solutions" or programmers exercises.

The init-script could be something like this:
```
#!/bin/bash
test -f beep || exit 0
case "$1" in
 start)
   python /usr/bin/beep.py [keyboard] [wavefile] &
   echo $! > /tmp/.beep-PID
   ;;
 stop)
   kill `cat /tmp/.beep-PID`
   ;;
 *)
   echo "Uso: /etc/init.d/beep start|stop"
   exit 1
   ;;
esac
```

This way:
[LIST=1]
[*]It works at the login screen
[*]It's getting killed properly at shutdown
[*]There are no security issues (as far as I can see)
[/LIST]

---

### Post by N!coz on 2010-01-05
> **Martje_001 said:**
> Realzippy: I didn't mean to offend you of course. If I did: I hereby apologize. It just that I sometimes get fed up with bad "solutions" or programmers exercises.

The init-script could be something like this:
```
#!/bin/bash
test -f beep || exit 0
case "$1" in
 start)
   python /usr/bin/beep.py [keyboard] [wavefile] &
   echo $! > /tmp/.beep-PID
   ;;
 stop)
   kill `cat /tmp/.beep-PID`
   ;;
 *)
   echo "Uso: /etc/init.d/beep start|stop"
   exit 1
   ;;
esac
```

This way:
[LIST=1]
[*]It works at the login screen
[*]It's getting killed properly at shutdown
[*]There are no security issues (as far as I can see)
[/LIST]

Thanks boy for all the help that you gave me !
I have not understand how i can check the pid's ?! 
When i have the pids i cane use the script posted or not?

---

### Post by N!coz on 2010-01-08
Because i'm not able to run correctly this script, but anyhow the beep is run correctly , i put the solved tag. I want to thanks martje and realzippy for all the help. Thanks guy

---

