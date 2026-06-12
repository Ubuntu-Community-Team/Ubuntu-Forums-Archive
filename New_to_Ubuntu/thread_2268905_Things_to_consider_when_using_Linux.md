---
title: "Things to consider when using Linux"
date: 2015-03-12
forum: New to Ubuntu
---

### Post by RobGoss on 2015-03-12
Hello everyone, I have a simple question and would like your input. As a new Linux user what are some of the things I should be doing on a daily bases to keep my system safe?

I know about keeping my packages updated and adding a fire wall but is there some else I should be doing as a Linux user?

If you don't mind can you list a few things you do on a daily bases to keep your system safe.

Thank you so much

---

### Post by slickymaster on 2015-03-12
If you're a simple desktop user who only uses his computer for the most ordinary things, then this is the basic rule set:
[LIST]
[*]Immediately install security updates when you're notified;
[*]Do not install antivirus, as you *really* don't need it in Linux, unless you share files with Windows;
[*]Enable the firewall (sudo ufw enable) without further tweaks, unless you specifically need them;
[*]Stick to the official repo's as much as possible, and only deviate from them when strictly necessary and with much caution;
[*]Keep Java (both openJDK and/or Oracle Java) disabled by default in your browser, and only enable it when needed;
[*]Use your common sense. The biggest security threat is generally found between keyboard and chair.
[/LIST]

And please, do have a read at this forum sticky: [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by RobGoss on 2015-03-12
Hello and thank you for the list of things to consider when using Linux.

I'm new to Linux but not to navigating and using a computer. although I don't consider myself an expert I'm always looking for the best ways to keep things safe and seeing I'm new to Linux its even more essential now then ever.

You stated common sense is a factor to keep things safe and you are correct. Thank you so much.

---

### Post by coldraven on 2015-03-12
If you use Firefox and are concerned about security you can change the setting to delete cookies, history etc. when you exit .
Go to Edit>Preferences>Privacy and under Hisory choose "Custom". Then select whatever you want to be deleted.
Another way, which I do after Internet Banking or other sensitive transactions, is to press Ctrl+Shift+Delete. Then select cookies and history.

---

### Post by RobGoss on 2015-03-12
> **coldraven said:**
> If you use Firefox and are concerned about security you can change the setting to delete cookies, history etc. when you exit .
Go to Edit>Preferences>Privacy and under Hisory choose "Custom". Then select whatever you want to be deleted.
Another way, which I do after Internet Banking or other sensitive transactions, is to press Ctrl+Shift+Delete. Then select cookies and history.

Thank you so much for the browser tips I will keep it in mind.

---

### Post by dino99 on 2015-03-12
Hello Robert

if you can spend some free time , then go and read the links below (and their sub links) 
you will get an over view and understanding about Ubuntu (and Linux in general)
):P

---

### Post by RobGoss on 2015-03-12
> **9d9 said:**
> Hello Robert

if you can spend some free time , then go and read the links below (and their sub links) 
you will get an over view and understanding about Ubuntu (and Linux in general)
):P


Thanks for sharing the link I will view it shortly.

---

### Post by mastablasta on 2015-03-12
every now and then check the authentication and various other security logs. though logs are not a 100% sure way to discover suspicious activity, many times they try to break in in a simple way. though if you enabled the firewall you should be good to go.

---

### Post by gordintoronto on 2015-03-12
If you're new to Linux, several things will trip you up which have nothing to do with security:

 - Documents and documents are completely different folders,
 - I will suggest "paste this command into the Terminal" rather than tell you about 12 icons to click on,
 - we don't download drivers, most of them are built-in,
 - we don't go to a web site and download a program, we run Software Center (or Synaptic Package Manager).

Unless you click on foolish links, Linux will pretty much stay secure.

---

### Post by newb85 on 2015-03-13
Lots of great suggestions so far.

Also, generally avoid deviating from Ubuntu's built-in security model.  For example, while the restricted user permissions on system files may seem like a nuisance, they're there for security purposes.
Installing WINE brings in a possibility of running Windows viruses, but there a few steps you can take to pretty much ensure this doesn't happen.  (I avoid WINE, so I'm not one to give directions here.)

---

### Post by RobGoss on 2015-03-13
> **mastablasta said:**
> every now and then check the authentication and various other security logs. though logs are not a 100% sure way to discover suspicious activity, many times they try to break in in a simple way. though if you enabled the firewall you should be good to go.

Thank you so much for the helpful link

---

### Post by RobGoss on 2015-03-13
> **newb85 said:**
> Lots of great suggestions so far.

Also, generally avoid deviating from Ubuntu's built-in security model.  For example, while the restricted user permissions on system files may seem like a nuisance, they're there for security purposes.
Installing WINE brings in a possibility of running Windows viruses, but there a few steps you can take to pretty much ensure this doesn't happen.  (I avoid WINE, so I'm not one to give directions here.)

Hello and thank you for your input, Yes I have three different installs of Linux on separate machines and I have Wine installed on just one installation but I don't really like it because it reminds me to much of Windows.

The whole purpose of me moving to Linux is because they do things so differently I suspect I will be removing it shortly.

---

### Post by RobGoss on 2015-03-14
Thank you all for some great starting tips I will refer to them as I lean to love Linux......

---

