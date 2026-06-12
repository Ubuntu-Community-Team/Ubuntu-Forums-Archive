---
title: "[SOLVED] Suspend/Hibernate not working"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by alexham on 2008-09-19
Hi,

I am experiencing very annoying problem with Suspend and Hibernate functions.  I really need Suspend, because I don't want to run the computer all day and I need to check my emails several times daily and don't want to have to go through the lengthy start up each time.

Suspend works sometimes, then it does not and I cannot establish the pattern. When it does not work it goes into shut down, then the password menu appears and I am back in the programme.  At other times the monitor goes blank, but the drives continue to run and the only way to get out of that is to soft-reboot.  Hibernate is even more "temperamental".

Giving myself permission to Suspend seems to have no effect on anything.

Thanks in advance,

Alex

---

### Post by w.g.hanna on 2008-09-19
similar but not exact problem . . . .

relatively new ubuntu user, and ubuntu is my first and so far only linux distribution. i'm running it on a hp pavilion a6500f desktop. i run ubuntu and ubuntu studio on different partitions. this primarily pertains to the standard version, though i don't know if i'd have this problem with studio because as of yet i havn't really experimented with it.

I used the power saving settings to go into power saving mode after 20 minutes. the computer powers down, and the green power button on the top of the tower turns amber. most of the time, i can wake the computer up by just hitting a button on the keyboard or shaking up the mouse.

twice yesterday, it wouldn't wake up no matter what i tried, requiring a hard boot. any ideas of what could be causing it, if it could be bad for my computer, and how it can be corrected?

and generally - in terms of being good for your computer - whats the best way to manage power? turn it off at the end of the night or let it hibernate?

i worry that having to hard boot the computer two or three times a day will shorten the life of my computer so i'm thinking of making a switch if i can't fix it. i strongly prefer gnome to kde or xfce, but you think that might be the root of it? and i hope it doesn't come down to trying another distro - although i am the phase of my linux experimentation where i've had some real success with ubuntu and am curious about what else is out there. . . . .

any ideas would be appreciated

---

### Post by k33bz on 2008-09-19
> **alexham said:**
> Hi,

I am experiencing very annoying problem with Suspend and Hibernate functions.  I really need Suspend, because I don't want to run the computer all day and I need to check my emails several times daily and don't want to have to go through the lengthy start up each time.

Suspend works sometimes, then it does not and I cannot establish the pattern. When it does not work it goes into shut down, then the password menu appears and I am back in the programme.  At other times the monitor goes blank, but the drives continue to run and the only way to get out of that is to soft-reboot.  Hibernate is even more "temperamental".

Giving myself permission to Suspend seems to have no effect on anything.

Thanks in advance,

Alex
I havnt got suspend or hibernate to work on my laptop. Although I will lock my computer up, I dont know if that is a viable option for you or not. ```
[CODE]<Ctrl> + <Alt> + L
```[/CODE]

---

### Post by alexham on 2008-09-20
Locking the screen is not an option because the drives continue to run, although it is useful if you want to prevent unauthorized access, which is not one of my problems.

I need to be able to log on quickly, have a look at one or two emails and log off and I need to do that 5 or 6 times a day.  Therefore, if the Suspend cannot be made to work reliably, it will be a real tragedy for me as I would then have to rely entirely on Windows and not use Ubuntu at all.

I like ubuntu in every way, but it is very strange, to sat the least, that  a new version has been released with such a basic flaw.

I do hope that some real experts are reading this.

Thanks,

Alex

---

### Post by alexham on 2008-09-21
> **w.g.hanna said:**
> similar but not exact problem . . . .

I used the power saving settings to go into power saving mode after 20 minutes. the computer powers down, and the green power button on the top of the tower turns amber. most of the time, i can wake the computer up by just hitting a button on the keyboard or shaking up the mouse.

twice yesterday, it wouldn't wake up no matter what i tried, requiring a hard boot. any ideas of what could be causing it, if it could be bad for my computer, and how it can be corrected?

and generally - in terms of being good for your computer - whats the best way to manage power? turn it off at the end of the night or let it hibernate?

i worry that having to hard boot the computer two or three times a day will shorten the life of my computer so i'm thinking of making a switch if i can't fix it. i strongly prefer gnome to kde or xfce, but you think that might be the root of it? and i hope it doesn't come down to trying another distro - although i am the phase of my linux experimentation where i've had some real success with ubuntu and am curious about what else is out there. . . . .

any ideas would be appreciated

After much experimentation, I think I may have found the way to make it work.

Go to System/Administration/Authorisations then scroll down to Power Management and click on Suspend the system.  Click on "Grant" in the menu on the right and select yourself, then close.

Then go to System/Preferences/Power Management  and click on General tab and select Suspend when Suspend button is pressed. I have also selected Shutdown when power button is pressed. Then Reboot.

if you get a blank screen when coming out of a suspend mode, just press <Enter> and the password menu should appear.

Hibernate button will not work but all other do on my system.

I hope this helps.

Alex

---

