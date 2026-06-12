---
title: "installation button does nothing"
date: 2017-04-22
forum: New to Ubuntu
---

### Post by johnny7oak on 2017-04-22
I cannot install chrome or any other applications.  I have recently installed Ubuntu, but experimented with it like in 2006.  this interface is way nice, but how the heck do I install something.  Terminal pass-code goes really quick, and the drag and drop option just gives me the button that says install or website.. website buttons work.  install does nothing.

any suggestion?

-johnny7oak

---

### Post by vasa1 on 2017-04-22
> **johnny7oak said:**
> ...  Terminal pass-code goes really quick ...
What does "Terminal pass-code" mean?

---

### Post by Bucky Ball on 2017-04-23
Welcome. You can install things using Ubuntu Software (or might just be called 'Software') or open a terminal and install things that way. If you open a terminal and install Synaptic Package Manager you can also use that to install things.

```
sudo apt install synaptic
```

You will then find Synaptics in the 'Dash'. Many prefer it and some have changed to it because the Ubuntu Software app was a bit buggy I believe. I don't use straight Ubuntu or Ubuntu Software so unsure of the state of play there.

---

### Post by Impavidus on 2017-04-23
Installation of chrome works somewhat differently than installation of most other software. Most software comes from the Ubuntu repositories, but chrome comes from a stand-alone .deb.

---

### Post by Bucky Ball on 2017-04-23
Of course. ;) Perhaps Chromium?

---

### Post by sp40140 on 2017-04-23
Do you mean to say that when you double click on the chrome deb file which you downloaded, It opens in "software" and there is install button and that button doesn't do anything?

if this is correct, you can install it with following command..
sudo dpkg -i <fillename>.deb

---

### Post by vasa1 on 2017-04-23
Why the focus on Chrome? OP wrote:> I cannot install chrome or any other applications.

---

### Post by johnny7oak on 2017-04-25
well the sudo passwd command always prompts in like 5 seconds... that was all I meant by passcode.  Besides that terminal passwd thing is horrible with a strong passcode.  is "t" an illegal passwd character?

Edit: I will look for synaptic on the web.  I'd do the sudo dpkg, but again the sudo passwd thing is horrible.

I installed synaptic, that installed fine.  Still not doing anything when I try to click "install" the "Ubuntu software" utility window.  I kind of wanted "steam" as well.  I don't like having to log out to play master of orion 1. I really like that Ubuntu controls the dual boot option.  Windows 10 was awful on the other machine.  I found out that the BIOS is technically compliant to USB install, but the board is not. Additionally either the ISO file was corrupt or the DVD disc burned wrong - forget add ins with a DVD burner only option.  So... I have only this machine to run Ubuntu on.  I have two of those flash memory sticks anyways, but one is going to my brother for his birthday.  He is an industry IT meaning he favors sequel server and Microsoft.net.  Probably won't touch it.  He told me in the industry you go one way or the other.  I am not a Unix knowledge base... well not yet.  I kind of thought that a Java compiler would run nice on Ubuntu, any suggestions?  I am getting alright with JavaScript, but would very much like to load by line from a file.

Edit#2: Went with JDK downloading now.. hope it installs.  I am going to attempt the demos tutorials too.

---

### Post by deadflowr on 2017-04-25
> Besides that terminal passwd thing is horrible with a strong passcode. is "t" an illegal passwd character?
Huh?
How strong a password?
No, t is fine.

---

### Post by wildmanne39 on 2017-04-25
Please keep the thread to one issue per thread so when it is solved searches will actually find the issue they were looking for. We have a one issue per thread rule.

Please stay on topic.
Thanks

---

### Post by johnny7oak on 2017-04-27
maybe it "s" anyways I get there in terminal for passwd and it kind of skips out.  so no ability to enter the passwd the next attempt is like 5 seconds.  the strong password/passcode is rather much just the requirement for the Ubuntu 16x version.

---

### Post by leunam12 on 2017-04-27
If you don't want to enter your password you can always buy a USB fingerprint reader.

[https://rover.ebay.com/rover/1/711-53200-19255-0/1?icep_id=114&ipn=icep&toolid=20004&campid=5338055221&mpre=http%3A%2F%2Fwww.ebay.com%2Fsch%2Fi.html%3F_odkw%3Dusb%2Bfingerprint%26_osacat%3D0%26_from%3DR40%26_trksid%3Dm570.l1313%26_nkw%3Dusb%2Bfingerprint%2Breader%26_sacat%3D0](https://rover.ebay.com/rover/1/711-53200-19255-0/1?icep_id=114&ipn=icep&toolid=20004&campid=5338055221&mpre=http%3A%2F%2Fwww.ebay.com%2Fsch%2Fi.html%3F_odkw%3Dusb%2Bfingerprint%26_osacat%3D0%26_from%3DR40%26_trksid%3Dm570.l1313%26_nkw%3Dusb%2Bfingerprint%2Breader%26_sacat%3D0)

---

### Post by johnny7oak on 2017-04-27
that works for terminal?

---

### Post by leunam12 on 2017-04-29
It works for me with fprint. the fingerprint-gui program didn't work for me on the terminal, but fprint works

---

### Post by johnny7oak on 2017-04-30
I don't have problem logging in, its just terminal.   I got it now.  apparently sudo passwd doesn't show.  I got a program installed.  Can I change this to solved?

---

### Post by deadflowr on 2017-04-30
> Can I change this to solved?
Go to the top of this page (right above the very first post on the right side area), to the Thread Tools and go to the entry within for Mark this Thread as Solved.

---

