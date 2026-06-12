---
title: "script privlegedes"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by NaF on 2008-09-06
I have a machine that i turn on when i go to sleep, which loads a random movie - and turns off 2 hours later. I wanna map say "esc", to load a script which 
```
sudo shutdown -c
```
to stop an incoming shutdown. But i wont be able to write the root password, and the command requires it. How do I go around with this?

---

### Post by RealPSL on 2008-09-06
One option there is to allow yourself access in the sudoers file to run the shutdown command without needing to enter a password. The other options generally involve feeding your password to "expect" scripts which I do not like.

First edit the sudoers file with ```
sudo visudo
``` this assumes you are an admin.

Add the line > Cmnd_Alias	SHUTDOWN = /usr/sbin/shutdown under the command alias specification section.

Then at the bottom add the line
> %admin	ALL = NOPASSWD: SHUTDOWN

You can replace %admin with your own user name but I like using groups.

---

### Post by Cheesehead on 2008-09-06
A much easier solution is to:
1) Remove all references to sudo from your script.
2) Run *the script* as sudo - 'sudo script.sh'

---

### Post by NaF on 2008-09-06
> **RealPSL said:**
> One option there is to allow yourself access in the sudoers file to run the shutdown command without needing to enter a password. The other options generally involve feeding your password to "expect" scripts which I do not like.

First edit the sudoers file with ```
sudo visudo
``` this assumes you are an admin.

Add the line  under the command alias specification section.

Then at the bottom add the line


You can replace %admin with your own user name but I like using groups.
Don't quite follow - why don't you like this method?

> A much easier solution is to:
1) Remove all references to sudo from your script.
2) Run the script as sudo - 'sudo script.sh'
I only have 4 keys available, so no matter when the sudo is called, I can't type out the password.

---

### Post by forger on 2008-09-06
Weird, why does it shut down itself? Why don't you disable whatever makes it shut down?

---

### Post by NaF on 2008-09-06
> **forger said:**
> Weird, why does it shut down itself? Why don't you disable whatever makes it shut down?

I've made it shutdown on it's own - it's just if i'm watching movies beyond the 2h and don't wanna fall asleep i want the option to disable it.

---

### Post by forger on 2008-09-07
So that's the culprit :)
Couldn't you also make your script pop up a timed question using zenity:

```
ask=`zenity --question --text="Will shutdown. Proceed now?"`;
if [ $? -eq 0 ]
then
	echo "You said OK"
	echo "Do more commands"
else
	echo "You said Cancel"
	echo "Do some more commands"
fi
```

(Note: I think the ";" at the end is important)

---

### Post by forger on 2008-09-07
or this script:
```
(for a in `seq 1 100`; do echo $a; sleep 0.1; done) | zenity --progress --percentage=0 --auto-close --auto-kill --title="Shutdown initiated" --text="Will shutdown in 10 seconds. Press cancel to abort"

shutdown -H now
```

---

