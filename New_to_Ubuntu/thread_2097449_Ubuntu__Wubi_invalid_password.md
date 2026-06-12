---
title: "Ubuntu / Wubi: invalid password"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by marshmallow1 on 2012-12-23
Hello community!!

After having Ubuntu working fine (for a short while), alongside Windows 7, I re-installed Ubuntu using Wubi. At one stage, one gives Wubi a username / password combo, but this combo did not work when Ubuntu loaded. I did this again (re-install using Wubi) to make sure it wasn't just being silly with caps lock etc. I am looking for advice on how to proceed.

I note that this has been posted before (so please don't smash me for re-posting):
[http://ubuntuforums.org/showthread.php?t=1041232](http://ubuntuforums.org/showthread.php?t=1041232)
[http://ubuntuforums.org/showthread.php?t=1805548](http://ubuntuforums.org/showthread.php?t=1805548)

Responding to advice in the first note above:
When I boot up, I have the option of Windows / Ubuntu under the heading "Windows Boot Manager". ESC here restarts the computer, but I arrive at the same menu a moment later

And to the second note above:
I'm not sure how to boot up in recovery mode and / or bring up a terminal

Thank you all, I hope Santa brings you something nice.

John

---

### Post by Frogs Hair on 2012-12-23
Hello and Welcome

I have not watched a Wubi installation with 12.10 as I have with other versions since 9.10. I would delete and down load a new version of Wubi because after seeing and helping with many Wubi installations what you described as never happened.I suspect Wubi.exe or that _it was not run as administrator_.  [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)   

To remove the current the installation do the following.

1.Remove Ubuntu from programs and features.

2. It is a good idea to run defrag and disc cleanup but not necessary. 

3_.right click and run wubi as adminisratior_

---

### Post by bcbc on 2012-12-24
With recent versions of Wubi, the grub menu is hidden and the submenus have changed as well. 

To make the grub menu appear you need to hold down the Shift key after selecting Ubuntu. Then after it appears, and you can select "Advanced Options" at which point you'll see the recovery mode (2nd entry).

Wubi has you enter a username and password, but confusingly it will prompt you to logon with your Windows user name. This sometimes tricks people into entering a different password. 

e.g. Windows name "John". The idea is that the Wubi username would be "john" (has to be lowercase) and then Ubuntu asks "John" to logon. But if the Windows name is Mary, and you enter "john", then it would be a little confusing to be prompted with "Mary" when you log onto Ubuntu. The trick is to use the same password that you used when you installed with Wubi, regardless of what you see as the username.

Or if you truly believe that it somehow forgot your password, you can change it using the recovery mode method, but I haven't seen any repeatable test showing that the password is not honoured. If you can do that, then you should file a bug report.

---

### Post by marshmallow1 on 2012-12-24
Thank you Frogs Hair, the steps listed worked. You were correct, it appears I did not run Wubi as admin, despite the instructions making this _perfectly_ clear. I'm very embarrassed, sorry to waste ppl's time.

Thank you bcbc, I did not know about the shift feature.

I will edit original post to say solved.

---

### Post by Elfy on 2012-12-24
You can mark thread as solved in Thread Tools at the top :)

---

