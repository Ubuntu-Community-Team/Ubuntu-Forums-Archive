---
title: "No Chineses character after upgrade to 14.04"
date: 2014-09-01
forum: New to Ubuntu
---

### Post by czgirb on 2014-09-01
I recently upgrade my **12.04 "Precise Pangolin"** to **14.04 "Trusty Thar"**.
After that, my input for Chinese Character is stopped working.
Within the panel, i still able to see all **listing of possible Chinese Character input methods**,
 when typing ... it shows the available characters, but after selecting ... the text  editor only shows **[Invalid UTF-8]**. 

  I've tried:


> open a terminal
sudo apt-get install language-selector-gnome

ibus-daemon -drx


and
> delete Chinese input text entry setting
sudo apt-get remove ibus-pinyin

sudo apt-get install ibus-libpinyin


and still there is no **the available chinese input method** to be selected within my **text entry setting**
please guide me ...

---

### Post by elim-qiu on 2014-11-01
I had 3 machines fresh install and/or update to 14.4, all of them have broken Chinese Pinyin input. Well interface shown fine, but worked like junk. Tried all suggested fixes but none of them working.

I want to Chinese Ubuntu community and got impression: most people given up and turned to Google pinyin etc.

Really hope 14.10 resolve the issue.

---

### Post by Bucky Ball on 2014-11-01
> **elim-qiu said:**
> 

Really hope 14.10 resolve the issue.

Why not install it on another partition or as a virtual machine and find out? :-k

---

### Post by GrouchyGaijin on 2014-11-01
I think I had something similar to your experience although it was with Japanese input.  I had used Anthy for years and then with 14.04 I had all kinds of input problems.  I ended up changing to Mozc.  I don't exactly know what caused the problem, but after running the Mozc setup utility I can once again type in Japanese (&#26085;&#26412;&#35486;).

---

### Post by riverguy99 on 2014-11-02
If it worked fine in 12.04, a simple and effective fix would be to ditch 14.04 and return to good old, proven and rock-solid 12.04.  That's what I had to do for a lot of similar reasons.  14.04 really offers nothing compelling to make the "upgrade" worthwhile, especially if it is causing you problems.

---

### Post by Bucky Ball on 2014-11-02
I have changed the title of your thread to improve your chances of support. Good luck.

Most people here have a problem with one thing or another so generic thread titles don't always attract much attention. ;)

---

### Post by Penguin360 on 2014-11-03
In iBus Preference, change "Half/full width" to "Half", then restart iBus, it should fix the problem.

Or when the floating bar appears, click on the second icon to change it to Half width if it is Full width.

See the attached screen shot.

---

### Post by elim-qiu on 2014-11-26
> **Penguin360 said:**
> In iBus Preference, change "Half/full width" to "Half", then restart iBus, it should fix the problem.

Or when the floating bar appears, click on the second icon to change it to Half width if it is Full width.

See the attached screen shot.

Just tried, not working.

The sticky  problem is that it automatically split any pinyin of a Chinese Character into an array of 'guess_units' ,  insert letters to the guess_units according to some logic that guarantees the miss-interpreting of your pinyin inputs

If you go   Linux Chinese programming forums, people will tell you that no current input method is good enough compare with the old gold age of Ubuntu 12.*

---

### Post by Penguin360 on 2014-11-26
> **elim-qiu said:**
> Just tried, not working.

The sticky  problem is that it automatically split any pinyin of a Chinese Character into an array of 'guess_units' ,  insert letters to the guess_units according to some logic that guarantees the miss-interpreting of your pinyin inputs

If you go   Linux Chinese programming forums, people will tell you that no current input method is good enough compare with the old gold age of Ubuntu 12.*

I have no idea why it didn't work for you, but it worked for me. Maybe because I am using English version of Ubuntu, and you are using Chinese version?

---

### Post by flaymond on 2014-11-26
Do you ever try Ubuntu Kylin? It's suitable for Chinese users. Check it out -


[http://www.ubuntu.com/desktop/ubuntu-kylin](http://www.ubuntu.com/desktop/ubuntu-kylin)

---

### Post by elim-qiu on 2014-11-28
> **riverguy99 said:**
> If it worked fine in 12.04, a simple and effective fix would be to ditch 14.04 and return to good old, proven and rock-solid 12.04.  That's what I had to do for a lot of similar reasons.  14.04 really offers nothing compelling to make the "upgrade" worthwhile, especially if it is causing you problems.

I tried 13.04 today, after a fresh install, I cannot connect to package repository, so cannot download and install many things needed. I don't know if go back further to 12.04, what'll happen.

I'll try 12.04 if it can provide me most of what I needed.

Thanks,

Elim

---

### Post by Bucky Ball on 2014-11-28
@elim-qiu: 13.04 is no longer supported, thus the issues you're having. Please install 12.04 LTS or 14.04 LTS, both supported for five years, or 14.10 which has nine months support. Good luck.

---

### Post by monkeybrain20122 on 2014-11-29
Chinse input in ibus is kind of broken after 13.04 [http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm](http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm), see 'warnings'. 

Use fcitx instead, it is the default input method for Ubuntu Kylin and reputed to be the best Chinese input method 
[http://pv22.com/archives/4b07be3c60da3f48b380f3f0/](http://pv22.com/archives/4b07be3c60da3f48b380f3f0/)
According to the developer you should get fctix from its nightly ppa instead of the standard repo
[https://launchpad.net/~fcitx-team/+archive/ubuntu/nightly](https://launchpad.net/~fcitx-team/+archive/ubuntu/nightly)

---

### Post by Clopper Almon on 2015-01-20
I had the same problem. After some searching around on the Internet, I found the procedure described below which fixed the problem for me when using the Unity desktop under Ubuntu 14.04 (as of Jan 17, 2015). Here are the steps:

1. Delete the Chinese input text entry setting. To do this, click on the En button in the top menu bar. Click on "Text Entry settings ..." Then click on "Chinese" in the pane on the left side of the window. Then click the  -  button at the bottom of that window. (At first, this - button did not work, but on the third or fourth try it did.) "Chinese" disappears from the pane.
2. Open a terminal window and in it do:
        sudo apt-get remove ibus-pinyin
        sudo apt-get install ibus-libpinyin
    Close the terminal.
3. Reboot
4. Click the En button in the top menu bar.  Select "Text entry settings ...". Click on the + sign below the pane on the left and select "Chinese (intelligent pinyin)" from the drop-down list. Close the window.

I would also mention that you can control the size of the candidates and the font in which they are displayed by clicking on the En button in the top menu bar, then on "Text entry settings ..." Be sure that the box "Using custom font" is checked. What looks like one button to the right of it is really two buttons. Click on the left half for the button and pick the font you want for the candidates. I like Arial for clarity; it is also quite complete.  Then to set the size of the canditates, click on the right side of the button (where there is probably a number) and from the drop down list, pick a font size. I like 20, which gives what looks to me like about 14 point characters. 

Sadly, ibus still does not work for me under the Gnome desktop, which, in general, I much prefer.  However, when trying to input Chinese characters from pinyin, the candidates are not shown at present under Gnome.

---

### Post by Penguin360 on 2015-01-21
> **InterProg said:**
> Do you ever try Ubuntu Kylin? It's suitable for Chinese users. Check it out -


[http://www.ubuntu.com/desktop/ubuntu-kylin](http://www.ubuntu.com/desktop/ubuntu-kylin)

I agree. Instead of spending time on fixing the issue, Chinese users should use Ubuntu Kylin, which has several Chinese input methods built-in plus some software popular among Chinese users.

---

### Post by monkeybrain20122 on 2015-01-21
> I agree. Instead of spending time on fixing the issue, Chinese users  should use Ubuntu Kylin, which has several Chinese input methods  built-in plus some software popular among Chinese users.                 


I really disagree with this. 

You may want Chinese support because you use Chinese occasionally but not using a full blown Chinese OS. Kylin is a vast overkill for someone like me. I would like the option to use Chinese sometimes, but can do without it. However I can't deal with an all Chinese OS :) (my eyes glazed over when I tried to troubleshoot my dad's Chinese Windoze machine)There is a huge population of Chinese Canadians/ Americans/ Britons etc who are more comfortable with English than Chinese but nevertheless would have occasions to use Chinese. Or how about someone trying to learn Chinese? I am sure you can think of many other scenarios why you would want an English OS with decent Chinese input support instead of going all the way to a Chinese OS. :)

Instead of going Kylin all one needs is to replace Ibus with fctix, which is the default input method of Kylin.

---

