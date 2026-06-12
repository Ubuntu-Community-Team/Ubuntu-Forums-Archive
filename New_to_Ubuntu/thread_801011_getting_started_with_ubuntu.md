---
title: "getting started with ubuntu"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by jsdieorksw on 2008-05-20
I recently just purchased a new dell laptop installed with Gutsy Gibbon and I'm still trying to get the hang of things. Just a few things I'm trying to get going. I saw that the ubuntu community just started a beginner team, and I just gotta say that you guys are amazing.  The sense of community that is felt here is wonderful! 
I have just a few issues. 
1. I need help properly setting up Mozilla Thunderbird. 
2. I need help properly setting game emulators i already installed through the Synaptic Package Manager. 
3. Using S-video to use my computer to watch movies on TV. 

If any help or advice is possible i would greatly appreciate it.

---

### Post by jakupl on 2008-05-20
I can only help you with your first question.

What email do you use? gmail, hotmail or something else?

---

### Post by jsdieorksw on 2008-05-20
I have a gmail account

---

### Post by jakupl on 2008-05-20
> **jsdieorksw said:**
> I have a gmail account

try to follow this.

[http://email.about.com/od/mozillathunderbirdtips/qt/et121604.htm](http://email.about.com/od/mozillathunderbirdtips/qt/et121604.htm)

let me know it it fails.

EDIT: this might prove more useful

[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)

---

### Post by avtolle on 2008-05-20
> **jsdieorksw said:**
> I have a gmail account
May I suggest going to gmail, under "help" as I recall, and look for the specific instructions given therein for configuring Thunderbird? That's what I've done, and it's worked flawlessly every time.
EDIT: [http://mail.google.com/support/bin/answer.py?answer=77662&topic=12814](http://mail.google.com/support/bin/answer.py?answer=77662&topic=12814) is a link to set up Thunderbird 2.0 for IMAP, as an example. One step beyond the general information link that jakupi posted *supra*. :-)

---

### Post by jsdieorksw on 2008-05-20
I'm not currently with my laptop, i'll post back once I tried it. Thanks!

---

### Post by om1 on 2008-05-20
for #3

what graphic card do you have... if it is nvidia type this in terminal
```
sudo apt-get install nvidia-xconfig
```

but you will need to have your nvidia driver installed

---

### Post by jsdieorksw on 2008-05-20
I have a Intel Graphics Media Accelerator X3100, not sure if this is what was needed but I think this is my graphics card

---

### Post by om1 on 2008-05-20
> **jsdieorksw said:**
> I have a Intel Graphics Media Accelerator X3100, not sure if this is what was needed but I think this is my graphics card

yeah that is what was needed... ill see if i can find info on how to configure the svideo out

---

### Post by jsdieorksw on 2008-05-20
I'm in the process of setting up my email but I've hit a snag, I had someone help me earlier here at home and she told me to set up my server type as pop but i now know this to be incorrect, how do I change the server type to imap so i can set up my gmail account with thunderbird? Thanks!

---

### Post by avtolle on 2008-05-20
> **jsdieorksw said:**
> I'm in the process of setting up my email but I've hit a snag, I had someone help me earlier here at home and she told me to set up my server type as pop but i now know this to be incorrect, how do I change the server type to imap so i can set up my gmail account with thunderbird? Thanks!
If I understand your question, in your gmail account, go to settings, enable IMAP and save. You may need to disable POP, I cannot recall. BTW, in the link I posted earlier, specific instructions are given about setting all this up, complete with working links. Hope this is of assistance to you.

---

### Post by jsdieorksw on 2008-05-20
Yes, I'm using instructions that are in one of the links you posted,  but it says first i need to set my thunderbird account with a imap server type. I need to know how to change server type to imap in Thunderbird not in my gmail account itself, or does it matter? it's not really clear on how to do this.

---

### Post by avtolle on 2008-05-20
OK, first establish your settings in the gmail account to allow use of IMAP. Save. Then, open Thunderbird, and if you haven't started to set it up yet, go through the Wizard to establish your gmail account (under whatever name you decide to give it). Once the Wizard has finished, and you are at the Thunderbird page, click on the name you have given your gmail account. A menu of sorts will appear, select account settings (as I recall). Then, in the left box, click on server settings, and provide the information as to user name, etc., select IMAP, put in the port information from the gmail help, etc. When that's finished, again in the left box, click on smtp server, and provide the information there, remembering to edit the port to be used and the encryption method. When you finish with all that, it should be set up. I'm going from memory right now, hope this helps you.

EDIT: Most importantly, and something I omitted, print the instructions for configuring Thunderbird from the gmail help on this topic. If your printer isn't working, at least write down the ports to use, the encryption to be used, for both the IMAP and SMTP servers, the server names, e.g., imap.gmail.com, as this will be needed to configure Thundebird.

---

### Post by Exsecrabilus on 2008-05-20
> **jsdieorksw said:**
> I recently just purchased a new dell laptop installed with Gutsy Gibbon and I'm still trying to get the hang of things.
Am I reading this right? You have Ubuntu 7.10 Gutsy Gibbon installed when a new version just came out?
Head over to Update Manager and upgrade to Ubuntu 8.04 LTS Hardy Heron now!

:D :D :D :D :D

---

### Post by jsdieorksw on 2008-05-20
I went ahead and used the pop server, after some searching I saw that I could just leave the way it was and just change my gmail settings.  I followed the instructions and I'm almost there, I can now send email but not receive.  When I click get mail i get an error (after at least 5 minutes of waiting) Connection to server pop.gmail.com was timed out.

---

### Post by avtolle on 2008-05-20
Check your port for POP under your Thunderbird setting, and make sure it agrees with what gmail wants (it is different for gmail than the normal default), as well as the encryption. Again, use the settings that gmail provides.

---

### Post by ebeckhusen on 2008-05-20
What version of Thunderbird do you have?  On mine (2.0.0.14) when you created a new account there was a button under account type where you could choose Gmail.  I don't think I had to set up anything else after going through their wizard.

---

### Post by jsdieorksw on 2008-05-20
I have the same version, i went through the wizard also but now i just can't receive email.

---

### Post by jsdieorksw on 2008-05-20
I just changed my port to 995 and settings to SSL and it works, thanks guys!

---

### Post by avtolle on 2008-05-20
> **jsdieorksw said:**
> I just changed my port to 995 and settings to SSL and it works, thanks guys!
Good to know. Enjoy.

---

### Post by ebeckhusen on 2008-05-20
> **jsdieorksw said:**
> I have the same version, i went through the wizard also but now i just can't receive email.

What do your setting say in Server Settings/Security Settings?  Mine is set to SSL and secure authentication is not checked.

Edit: Never mind, I see you fixed it :)

---

