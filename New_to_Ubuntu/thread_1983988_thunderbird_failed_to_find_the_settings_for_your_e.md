---
title: "thunderbird failed to find the settings for your email account"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by Houmie on 2012-05-21
Hi,

I have reinstalled Ubuntu 12.04. The first time I could simply start Thunderbird and put in my Gmail address and it would find the account settings and just work.

After the reinstallation, when I initially started TB, I cancelled the popup for setting up a new account. Now that I have tried to do again, it keeps saying 

"thunderbird failed to find the settings for your email account"

I have even uninstalled TB and reinstalled it without success. It makes no sense, I am using the same credentials to login per web and yes IMAP is enabled.

What is missing?

Thanks,

---

### Post by diddly3000 on 2012-05-21
i am having exact same issue. i installed 12.04 yesterday i am very new to ubuntu.
also thunderbird worked fine on windows but will not find settings for gmail on ubuntu :(

---

### Post by agillator on 2012-05-21
The information for your accounts is in your profile. Your profile on Ubuntu is a directory /home/<username>/.thunderbird/< 8 random character string>.default. After you install or upgrade your operating system the easiest thing to do is to run thunderbird once and immediately close it so it will create a profile it knows about, then copy the contents of the old profile to the new (overwriting the new). That saves all your account information, your emails, etc. If you are dual booting with windows and have thunderbird working properly on windows, you should be able to copy the profile from windows to ubuntu without any problem. If you have the windows partition mounted in linux so you can read it and write to it, you should be able use that copy of your profile so everything is the same regardless of which system you are running at the moment. To do that, change the default profile to a symbolic link pointing to the windows version of the profile. Of course BACK UP THE PROFILE before you do anything.

---

### Post by Houmie on 2012-05-21
> **agillator said:**
> The information for your accounts is in your profile. Your profile on Ubuntu is a directory /home/<username>/.thunderbird/< 8 random character string>.default. After you install or upgrade your operating system the easiest thing to do is to run thunderbird once and immediately close it so it will create a profile it knows about, then copy the contents of the old profile to the new (overwriting the new). That saves all your account information, your emails, etc. If you are dual booting with windows and have thunderbird working properly on windows, you should be able to copy the profile from windows to ubuntu without any problem. If you have the windows partition mounted in linux so you can read it and write to it, you should be able use that copy of your profile so everything is the same regardless of which system you are running at the moment. To do that, change the default profile to a symbolic link pointing to the windows version of the profile. Of course BACK UP THE PROFILE before you do anything.

Thanks for your answer. Well I have now deleted teh entire .ThunderBird directory from /home/<username>/.

Rebooted and have tried it again. Now starting Thunderbird the first time again, it will ask me for the settings. I carefully enter them and it still doesn't recognize Gmail any longer.

What is going on?

---

### Post by Rex Bouwense on 2012-05-21
Same problem here.  It has never happened to me before and I have been using Thunderbird for many years with many OS.  When I figure it out I will post back.

---

### Post by don762003 on 2012-05-21
Same problem here as well. Very strange, I had the 12.04 alpha version installed and there was no problem then I switched to Fedora 17. No I'm back and this problem occurs. :lolflag:

---

### Post by don762003 on 2012-05-21
Make sure the settings are correct. Mine just said .gmail.com for imap . So I put imap.gmail.com and put the ports in and configured everthing per this page [https://support.google.com/mail/bin/answer.py?hl=en&answer=78799]("https://support.google.com/mail/bin/answer.py?hl=en&answer=78799") and everything works now. You might not have to configure the ports though, just try imap.gmail.com and smtp.gmail.com . Hope this works for you too.

---

### Post by OrangeCrate on 2012-05-21
Reinstalled over the weekend, and ran into the same problem. My guess, it's just a Thunderbird server glitch. Here's another thread covering the same issue. Personally, I'll just check email accounts manually through my browser, until it's fixed.

[http://ubuntuforums.org/showthread.php?t=1983432&highlight=thunderbird](http://ubuntuforums.org/showthread.php?t=1983432&highlight=thunderbird)

---

### Post by Houmie on 2012-05-21
Hi,

I am the OP of this thread and thanks to your hints I have found the problem.

Something is wrong with the AUtomatic configuration, so when it says it cant be found. do this:

Add imap.gmail.com  (imap is missing in front of dot)
Port: 993
SSL: SSL/TLS
Auth: Normal Password

Add smtp .gmail.com (smtp is missing in front of dot)
port: 587 or 465
SSL: STARTTLS
Auth: Normal password
Username: full email address 

Now it works!! :guitar:

---

### Post by OrangeCrate on 2012-05-21
> **Houmie said:**
> Hi,

I am the OP of this thread and thanks to your hints I have found the problem.

Something is wrong with the AUtomatic configuration, so when it says it cant be found. do this:

Add imap.gmail.com  (imap is missing in front of dot)
Port: 993
SSL: SSL/TLS
Auth: Normal Password

Add smtp .gmail.com (smtp is missing in front of dot)
port: 587 or 465
SSL: STARTTLS
Auth: Normal password
Username: full email address 

**Now it works!!** :guitar:

Partial fix here. It worked on Gmail, but not Yahoo. It's no big deal for me, so, I'll just wait it out. Thanks for the workaround.

:)

---

### Post by Squeakees on 2012-05-22
Thanks Houmie!

---

### Post by Houmie on 2012-05-22
> **Squeakees said:**
> Thanks Houmie!


Hey you are welcome. I think this is the first time I could help someone on Ubuntu forums. :) I am a new convert myself. ;)

---

### Post by Antoon Stessels on 2012-11-05
It worked splendidly from the beginning on my pc at home, but my pc here at work (I run ubuntu 12.10 through wubi install) shows the same problem over and over. I've tried many solutions, but still, it doesn't seem to work.

The problem is also related to my not being able to use google talk in Empathy... I can create the online account, it seems to accept everything I enter, but when I launch Empathy, it just won't login...

---

### Post by MaGaM on 2013-01-29
Hi all,

Just to share my experiences on this problem: Houmie's solution worked for me. I was fooled by the thunderbird account detection interface. After it couldn't find the mail servers automatically, the screen appears in that you can enter addresses manually. In that screen I took the values of the dropdowns at the beginning of the IMAP and SMTP lines as the first part of the mail server addresses. Through this thread I realized that was not how it was meant. They mean the mail protocols used for incoming and outgoing mail. My employer's mail server addresses however also use imap and smtp as the first part of their addresses. That's how I was 'fooled'.
Clearly an interface usability issue which could be resolved by removing the contents of the 'Server hostname' field altogether or maybe just remove the first '.', so that one doesn't read the two fields as 'one'. Other solution could be to clearly designate the dropdowns are for selecting mail protocols.

Just my 2 cents. Hope it helps to 'defool' others. ;)

---

