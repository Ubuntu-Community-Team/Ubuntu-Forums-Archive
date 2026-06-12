---
title: "2nd monitor goes offline after Ubuntu login, only comes back when switching to Mirror"
date: 2021-04-19
forum: New to Ubuntu
---

### Post by misteryoyogi on 2021-04-19
After booting my computer *both* monitors go online, but after signing in, my secondary monitor goes offline as soon as the desktop appears.



[LIST=1]
[*]If I go to **Settings -> Displays**, both my monitors are correctly listed there, second remains offline though.
[*]If I run *nvidia-smi*, latest drivers are successfully installed (**Version: 460.56**)
[*]Made sure my Ubuntu is up to date.
[*]Secondary monitor works perfectly on Windows and Mac.



[/LIST]
The only way I get my secondary monitor back online is by switching to Mirror Mode in **Settings->Displays**, and a few seconds later the monitor is back. Then I switch back to *Join Displays mode* and I got my monitor setup working again. But this process can be annoying.


One last detail, I have two monitors:

[LIST=1]
[*]Ancor Comunications inc 22" (Primary)
[*]Samsung Electric Company 24"
[/LIST]

If I go to **NVIDIA X Server Settings** and into *X Server Display Configuration*, my Samsung monitor (secondary monitor) is selected under the *Selection* dropdown. 

[IMG]https://i.postimg.cc/YCr6Lpkx/video.png[/IMG]


Would anybody know what's going on? :(

---

