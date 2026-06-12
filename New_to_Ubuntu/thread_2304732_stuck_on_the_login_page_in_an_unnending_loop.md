---
title: "stuck on the login page in an unnending loop"
date: 2015-11-29
forum: New to Ubuntu
---

### Post by rogerbenney on 2015-11-29
I have a Lenovo Carbon 1 which I have had for almost a year. I put Ubuntu 14.04 LTE on it immediately and everything has worked well until yesterday. Windows is no longer on the machine
When logging on from suspension I did not get my usual page I got the purple page with X! carbon top left, the Ubuntu logo bottom left and the usual buttons top right.
On the left edge was the sign in box with my name and underneath is Guest session.
When I type in my password it comes back to the same page and I cannot get into my information.
I can open up the Guest Session but I want my own files etc.
I have read many forums on this and I have to add that pressing ctrl+alt+F1 does nothing so I cannot get into Terminal.
Can someone talk me through this and please bear in mind I am not experienced with some of the language used in reference to suggested fixes.
I have of course rebooted the computer many times to no effect.
Thanks
Roger

---

### Post by maglin2 on 2015-11-29
Try ctrl+alt+F2 to drop to shell login.

It sounds to me like .Xauthority may have become corrupted, so you may need to delete it and let it recreate - but I'm no expert so please wait for some better help to allow proper diagnosis before doing anything.

---

### Post by rogerbenney on 2015-11-29
Thanks for your advice but I cannot get ctrl alt f2 to do anything and my password though correct will not open the login

---

### Post by sandyd on 2015-11-29
Hi,

Have you tried using the recovery mode (accessible from the GRUB bootloader) to access root?

You can then go to /home/<username> and delete the file named .Xauthority
Something like
```

mount -o remount,rw /
cd /home/<username>
rm .Xauthority
```

You can also do this from a LiveCD if you cannot access the grub console.
In the LiveCD, mount the drive using the GUI, and then browse to /media/ubuntu in the terminal
Go to the mount point there, and you can browse to home/<username> and delete the file using sudo.
```

cd /media/ubuntu
ls
cd <mountpoint>
cd home/<username>
sudo rm .Xauthority

```

Note that <username> and <mountpoint> need to be replaced with the appropriate values.

---

### Post by rogerbenney on 2015-11-29
Hello and thanks for your full and informative reply!
"Have you tried using the recovery mode (accessible from the GRUB bootloader) to access root?"
Ok how do I access the GRUB bootloader to access root and from there to recovery mode on my x1 carbon please?
Lets start there as I dont have a CD/DVD player on this computer
Roger

---

### Post by sandyd on 2015-11-29
Hold down SHIFT during boot.

If it does not appear, then you will need to use a LiveCD/DVD.
That being said, you can "burn" the ISO onto a USB drive to avoid having to use a disc. I personally find it a bit more reliable that way anyways.

---

### Post by rogerbenney on 2015-11-29
Hello again,
I can get to root from grub bootloader

When I try to type in
cd /home/<username> THIS TELLS ME THIS A FILE DIRECTORY
rm .Xauthority  NO SUCH FILE

I am sorry but I really am out of my depth here and I simply need more instruction.
So far it looks as if I have not messed anything up but I still cannot log in
Roger

---

### Post by sandyd on 2015-11-29
Hi, you will need to replace <username> with your username.

If you don't know it, you can run
```

ls -l /home

```
and see which username (there should only be one if there is one user on the computer) belongs to you.

---

### Post by rogerbenney on 2015-11-29
Hello again
when I try to delete .Xauthority it tells me that it cannot remove as it is a read- only file system

---

### Post by Geoffrey_Arndt on 2015-11-29
In post #4m, sandy provides detailed instructions.   Did you prefix the remove command with sudo?

---

### Post by steeldriver on 2015-11-30
If you are doing this from recovery mode, you will need to remount the filesystem with read-write permissions before you can delete or modify any files

```

mount -o remount,rw /

```

In this case, sudo isn't required because you are already in a root shell

---

### Post by rogerbenney on 2015-11-30
Hi Geoffrey,
No I did not do this as I am trying it in recovery mode.
If I should please show me exactly what I type.
Thanks
Roger

---

### Post by sandyd on 2015-11-30
Fixed - sorry about that

---

### Post by rogerbenney on 2015-11-30
Hi Sandy,
This problem is anything but fixed!
I have done as you suggested through the Recovery system but I still cannot log in.
It is possible I am doing something wrong, very possible!

For instance in the GNU GRUB menu I chose "Advanced options for Ubuntu" and then I chose one many Ubuntu with Linux recovery mode options
This lead me to a Recovery Menu and I scrolled to root pressed enter and got the shell prompt.
From there I followed your instructions.
I hope you have time for me today and I apologise for my inexpertise in these skills!
Roger

---

### Post by sandyd on 2015-11-30
Hmm,
So not .Xauthority.

Lets check to see if your X session is spouting off some errors...
Run the following from recovery:
```

cd /home/<username>
cat .xsession-errors | more
cat /var/log/Xorg.0.log | more

```
Press the enter key a few times until the whole file is shown. If there are any errors, post them here.

Posting the errors may be a bit tricky, do you have a USB drive?

---

### Post by rogerbenney on 2015-11-30
What is the figure after Xorg.?.log
What I have using 0 is a lot of log and I dont know what the errors look like.
Should I record what comes on the screen after the xsession-errors?
At the moment I am taking pictures with my cell phone
Roger
How do I get out of where I am ?
Only way I find is ctrl alt delete

---

### Post by sandyd on 2015-11-30
Do you have a USB drive?

---

### Post by rogerbenney on 2015-11-30
yes I do but how do I load on to it unless from my phone?
Is the object I am asking about a 0,o or something else?
It is not clear
Roger

---

### Post by sandyd on 2015-11-30
We are going to transfer the files onto the USB, you can place the USB onto another computer and attach the files to your post. It is much easier to check for errors this way.

Plug in the USB and run the following
```

fdisk -l
```.

Post the output.

This will show all of the disks and storage devices on the computer and allow us to mount the USB drive to transfer the files.

---

### Post by rogerbenney on 2015-11-30
Do I type fdisk -1 on to the page I have been working on before or after I go in and get the files back up on teh screen?
And do I have the typing correct about that 0 or whatever it is. I need to know as I might be in teh wrong place
R

---

### Post by sandyd on 2015-11-30
The "l" is a lower case L, sort of looks like a 1 but it isnt :P

Doesn't really matter where you type it as long as it is in the recovery mode.

---

### Post by rogerbenney on 2015-12-01
Good Morning (here)
One thing I suddenly realize I might have mentioned is that I used Clam TK not long before all this started happening and there were 4 PUA"s three of which I quaranteened and one that would not go anywhere. That one is much talked about in the Forums and the general concensus seems to be that it is a flse positive, whatever that is.
Could this have anything to do with my login issue?

Roger

---

### Post by maglin2 on 2015-12-01
Was one of the PUA's **usr/share/mime/mime.cache**?

If so you will find a report here [http://ubuntuforums.org/showthread.php?t=2274088&page=2](http://ubuntuforums.org/showthread.php?t=2274088&page=2) of someone who deleted it, and then found 'I deleted mime.cache and now cannot get back into my user account  (administrator). At login it simply reverts back to the login screen  after less than a second.'

Sounds familiar, however I am not clear how you could have deleted it unless clam was running as root under sudo.

---

### Post by rogerbenney on 2015-12-01
it may have been but I am not sure any anyway I think I quaranteened them all byt the one which gave me no choices.
Roger

---

### Post by maglin2 on 2015-12-01
Quarantining would have the same effect as deleting I think - however usr/share/mime/mime.cache is owned by root, so I can't see how you could have done anything with it unless clam was running as root, and on my machine clam runs as the user who runs it.

If you wanted to explore this further you could boot from a live cd and use nautilus (Files) to see if usr/share/mime/mime.cache is present in your hdd install.

I would be inclined to just keep following sandyd's advice though, and provide the info requested.

---

### Post by rogerbenney on 2015-12-01
it may have been but I am not sure any anyway I think I quaranteened them all byt the one which gave me no choices.
Roger

Thanks for the advice.
I was wondering as I have the 14.04 program on a thumb drive from which I installed it originallly, if I could possible use that to re-install without loosing everything I have?
Thanks for all the help and I will be back ina a hour or so to proceed with whatever Sandy want me to do
Roger

---

### Post by sandyd on 2015-12-01
I'm actually curious, it might be that clamav quarantined something. There are 10 thousand things that could cause your system to act like this, so we will take a look at clamav.
Clamav is not that accurate and has false positives so it is a good idea to review what it is quarantining.

Go back to recovery
```

cd /home/<username>/.clamtk/
ls -l viruses

```

Any text surrounded by arrows need to be replaced with appropriate values.

---

### Post by rogerbenney on 2015-12-01
I will get on this when I get home.
Your last sentence about arrows and the need to be replaced with appropriate values- is this something I can do and if so what values?
Thanks Sandy, a bunch!

---

### Post by sandyd on 2015-12-01
> **rogerbenney said:**
> I will get on this when I get home.
Your last sentence about arrows and the need to be replaced with appropriate values- is this something I can do and if so what values?
Thanks Sandy, a bunch!

Same as the instructions before, you need to replace <username> with your username

If you don't remember it, run
```

ls /home
```
to show what usernames are on your system

---

### Post by rogerbenney on 2015-12-01
there is I hope a jpg of my clamtk viruses attached

Sorry that was a jpg of the clamtk viruses!

I have the thumb drive in teh computer but I do not know how to load information you want in teh recovery mode screen to it,so I sent you a jpg of the clam tk viruses

---

### Post by maglin2 on 2015-12-02
For the recent dates that just looks like a list of zip archives, which maybe isn't going to help much. I suspect it probably implies that they are part of firefox cache, and so of little relevance, but it's hard (for me at least) to know.

Perhaps try 'cat' instead on the actual history file to get a bit more info for sandyd on the path to the detection - ie type into your terminal

```
cat /home/rogerb/.clamtk/history/Nov-26-2015.log
```

---

### Post by rogerbenney on 2015-12-02
Hi ,
I typed in what you suggested and got "no such file or directory"

---

### Post by maglin2 on 2015-12-02
No log file then? Oh well, it probably wasn't important. On my system that command for a date which has a scan result gives the file path and detection:
```
~$ cat /home/dg/.clamtk/history/Dec-01-2015.log

ClamTk, v5.19
Tue Dec  1 18:50:21 2015
ClamAV Signatures: 4136034
Directories Scanned:

Found 0 possible threats (897 files scanned).

No threats found.
---------------------------------------------

ClamTk, v5.19
Tue Dec  1 19:27:29 2015
ClamAV Signatures: 4136034
Directories Scanned:
/home/dg/.cache/mozilla/firefox/h4kvtjek.default/cache2/entries

Found 1 possible threat (1648 files scanned).

/home/dg/.cache/mozilla/firefox/h4kvtjek.default/cache2/entries/377C6FB806895BE48A3549CE293D626EE55B8543      PUA.Http.Exploit.CVE_2015_1692  
```

On reflection you could try going about this a different way.
First
```
cd /home/rogerb/.clamtk
```
then
```
ls -l history
```
then
```
cat history/<date>.log
```
where you choose <date> according to the output of history (if any). Maybe there is none, but below is what I get as an example:
```
dg@dave-Aspire-7736:~$ cd /home/dg/.clamtk
dg@dave-Aspire-7736:~/.clamtk$ ls -l history
total 32
-rw-rw-r-- 1 dg dg  696 Dec  1 19:27 Dec-01-2015.log
-rw-rw-r-- 1 dg dg 2493 Nov  8 23:09 Nov-08-2015.log
-rw-rw-r-- 1 dg dg  395 Nov  9 11:24 Nov-09-2015.log
-rw-rw-r-- 1 dg dg  201 Nov 12 17:30 Nov-12-2015.log
-rw-rw-r-- 1 dg dg  198 Nov 13 18:59 Nov-13-2015.log
-rw-rw-r-- 1 dg dg  199 Nov 18 10:28 Nov-18-2015.log
-rw-rw-r-- 1 dg dg  201 Nov 20 10:19 Nov-20-2015.log
-rw-rw-r-- 1 dg dg  201 Nov 24 18:44 Nov-24-2015.log
```

---

### Post by rogerbenney on 2015-12-02
Well I got a bunch of files from the 2nd entry like the ones you portrayed, but on the 3rd entry you suggested I got "no such file or directory"

---

### Post by maglin2 on 2015-12-02
Don't really understand that without seeing the input/output. Maybe a date format thing?

Probably doesn't matter much anyway in respect of the main issue. We'll see what sandyd thinks when she returns.

Is all your personal data on this system (documents, pictures, email etc) backed up?

---

### Post by rogerbenney on 2015-12-02
No I am afraid not!

---

### Post by steeldriver on 2015-12-02
You seem to have reason to suspect that the issue was caused by inappropriately deleting the /usr/share/mime/mime.cache file (on the suggestion of clamtk) - have you actually checked whether the file is there or not?

```

ls -l /usr/share/mime/mime.cache

```

---

### Post by scoutchorton on 2015-12-02
> **rogerbenney said:**
> 
I have read many forums on this and I have to add that pressing ctrl+alt+F1 does nothing so I cannot get into Terminal.

roger, does your F1 key have other symbols on to it? My laptop keyboard has a ? on to it. If so, because you are at the login screen, Ubuntu thinks you going to do something, like adjust your brightness (like my computer).

Try looking next to control, alt, and super (windows key), and see if there is an "fn" key. If so, hit Ctrl + Alt + Fn + F1.

If not, maybe a key is sticky and you can go into the guest mode and use the on screen keyboard (my Ubuntu has Onboard (if that is default)). Then try the keys.

Hopes it helps!

Good luck! :D

---

### Post by rogerbenney on 2015-12-02
It says no such file or directory

My F1 key has sound off/on symbol on it.
I have a FN key, I have pressed Ctrl+Alt+Fn+F1 and nothing changes

---

### Post by steeldriver on 2015-12-02
> **rogerbenney said:**
> It says no such file or directory

Was that in response to my suggestion (i.e. listing the mime.cache file)? If so, please try

```

update-mime-database -V /usr/share/mime

```

If you are in a user-shell (rather than the recovery mode root shell) you will need to prefix that by sudo

```

sudo update-mime-database -V /usr/share/mime

```

---

### Post by rogerbenney on 2015-12-02
Actually when I press those keys the screen changes to black and I see in the top lh corner
ubuntu 14.04.3 LTS x1 Carbon tty1
Underneath that is X1 Carbon login but it doesnt like the password
Any thoughts?

Sorry yes I was replying to you.
I just tried what you suggested and I got the read only file system message 
I wonder if should have done this with my user name first?

---

### Post by steeldriver on 2015-12-02
Didn't we ask you to execute

```

mount -o remount,rw /

```

earlier? if you are working in the recovery mode root shell, please do so now if you haven't already - then try the update-mime-database command again.

If you could clarify whether you are in a root shell or not it will make things easier going forward

---

### Post by rogerbenney on 2015-12-03
Here is the result of updating the mime database
Hope this helps
Thanks for your help 
Roger
Photo attached

---

### Post by steeldriver on 2015-12-03
OK so if you

```

exit

```

from the recovery mode shell are you able to boot normally and login now?

---

### Post by rogerbenney on 2015-12-03
Yes it is working, I am reluctant to turn it off now but I suppose I should try.
Thanks so much to everyone.
Can you tell me what I did wrong so I NEVER do that again?
Should I deselect PUA's from the ClamTK program?
I do notice that I can turn off the functions of the F keys with the FN key- I wonder if that was an issue

I do notice that having restarted the computer now it does still go to Ubuntu login screen instead of my home page, but the login worked!!
Thanks to all again
Roger

---

### Post by maglin2 on 2015-12-03
In your position my first action would be to institute a regular backup regime for my data in case anything bad does happen in future - and it will eventually. Re-installing the OS itself is fairly quick and easy, but losing your data is a long term pain.

---

### Post by rogerbenney on 2015-12-04
i took your suggestion with some embarrassment and have used the back up feature . These PUA's- seems like they can be a problem, should I stop Clamtk from scanning for them and does quarantining them do as much harm as delete can do?

---

### Post by steeldriver on 2015-12-04
I think the thing to remember is that the 'P' in 'PUA' stands for is '**Potentially**'

It's always a good idea to search the web and/or get a second opinion from a trustworthy 3rd party before going ahead and deleting/quarantining what may be essential system files

---

### Post by Geoffrey_Arndt on 2015-12-04
One of the drawbacks (but required) to running Windows OS are the overhead security programs.    I run two dual-boot systems, but running any AV on Ubuntu is just a "non-starter" for me.    Too many hassles for virtually zero benefits.    The security risks of cross-pollinating a Windows virus from Ubuntu to the MS-OS's is extremely remote . . . especially for normal users.    Smart use of the internet is the best security.   So, this works for me, but each person should decide if AV and similar browser customizations are worth it.

---

