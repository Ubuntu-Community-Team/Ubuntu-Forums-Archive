---
title: "Why does hibernate work?"
date: 2020-12-12
forum: New to Ubuntu
---

### Post by uhqmcdyhga on 2020-12-12
I had been using 
```
sudo pm-hibernate
```
to hibernate in 18.04, it worked mostly.
I had some problems with the nvidia driver and it needed an updated kernel.  I updated to 20.04, that fixed it.
Then pm-hibernate would just lock the computer, if I look in the log it says 
```
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
kernel update inhibits hibernate (/var/run/do-not-hibernate present)
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: Returned exit code 1.
```
I updated everything just because the message had the word 'update' in it, I wasn't surprised when that didn't fix it.
I followed the instructions here [HTML]https://askubuntu.com/questions/6769/hibernate-and-resume-from-a-swap-file[/HTML]
Now
```
[FONT=inherit]sudo systemctl hibernate[/FONT]
```
did nothing, a few seconds after pressing enter I get a new prompt in terminal
```
sudo pm-hibernate
```
Still just locked the computer
I tried in frustration
```
sudo hibernate
```
This gave me a message in terminal about Tuxonice
Back to the logs and I have this
```
s2disk: Could not use the resume device (try swapon -a). Reason: No such device
```
(swapon -a does nothing)
I went here [HTML]https://wiki.archlinux.org/index.php/Uswsusp[/HTML] none of the files listed there are on the computer in /etc/
I did find a folder there that said hibernate with a file called tuxonice.conf that says 
```
NOTE: TuxOnIce is an improved version of suspend-to-disk which currently
            requires patching your kernel. For more information, see www.tuxonice.net
```
That site seems to have been sold or something...

I took the info from the uswsusp page and just put it into ususpend-disk.conf to see what happens.
now
```
sudo pm-hibernate
```
hasn't changed
```
[FONT=inherit]sudo systemctl hibernate[/FONT]
```
seems to work as expected
I didn't try ```
sudo hibernate
``` because I got something to work.

Now for the puzzle, why?  All three of these commands are me asking the computer to do the same thing and each gave a different response, pm-hibernate and hibernate seem to be connected.  Are they?  Should the pm-tools be removed since they don't work and seem to be old and unsupported or is that what is making systemctl work?

I did get this in the log
```
[ 4170.005611] Uhhuh. NMI received for unknown reason 28 on CPU 0.
[ 4170.005612] Do you have a strange power saving mode enabled?
[ 4170.005612] Dazed and confused, but trying to continue
```
I don't know how to check and if I do how do I tell the computer?

---

