---
title: "suddenly cannot print .odt files"
date: 2017-04-03
forum: New to Ubuntu
---

### Post by jerrydc on 2017-04-03
HP Photosmart 5520e suddenly stopped printing odt files.  The files are  labelled HELD in the printer que and I cannot get them out of held. Can  print pdf, web pages, etc. Have a wireless connection to laptop. Use Ubuntu 16.04 LTS and always install  security fixes and updates. The printer app on my laptop says "connected to  localhost."

Would appreciate help; am a newby.

---

### Post by yancek on 2017-04-03
First, start by opening a terminal and running the command:  lpc status all
See if you get any interesting/useful output.  Then try the command:  lpq  look for any output.  It should show any jobs pending.  If you want to remove them, use the command:

lprm 500  (replace the 500 with the actual job number from the lpq command)

Try printing a file from the terminal and see if you get any messages.  If you have a file named myfile.odt in /home/user try:

lpr /home/user/myfile.odt  watch the output for any useful information.
How are you trying to print?  From the machine the printer is attached to?  Seems weird it would stop printing specific file types.  Are you trying to print the .odt files in the same manner as the .pdf and others, from the same machine or another manner?

---

### Post by jerrydc on 2017-04-04
Have never used Terminal and cannot start now.  I'm retired and don't have the time to start another complex project.  Therefore, would have no idea what to look for or what looks peculiar or problematical if I followed your instructions.  Furthermore, I'm sure I would mess up everything if I tried to follow your suggestion.  Yes, it is peculiar that suddenly it would stop printing what it had been and as near as I can tell it is only .odt files.  Would appreciate suggestions using graphical interface.  If that would not work, thank you anyway.
Jerry


sorry, I use only a Lenovo laptop connected wirelessly to the printer.  Have been doing that for several years. The printer wireless connector button is lit. A four page printout from the HP says everything is good,  It seems strange to me, however, that the "Wireless Network Test Results" page states "No problems found" when father down it says "not connected" to the Internet.  I'm guessing though that has nothing to do with printing odt files that are in folders on my laptop.

---

### Post by KenUBF on 2017-04-09
Hi Jerry,

I know the Terminal can seem scary at first but the commands [COLOR=#000000]yancek told you to enter won't hurt your system. It's actually really easy. All you have to do is open the Terminal and copy/paste the commands they mentioned, one at a time. For example, I used [/COLOR]```
[COLOR=#000000]lpc status all[/COLOR]
```[COLOR=#000000] and I got the following output:

[/COLOR]```
Deskjet-2050-J510-series:    printer is on device 'hp' speed -1
    queuing is enabled
    printing is enabled
    no entries
    daemon present
```

That's it. And if you get that we can walk you through the other steps. There isn't any harm of messing up your computer since you're not using the root account.

---

### Post by HermanAB on 2017-04-10
Open your web browser and go to [http://localhost:631](http://localhost:631) which is the CUPS management console.

In there, select the printer and delete the documents that are on hold, put it back online and print a test page.

Once that works, you are back in business.

---

### Post by jerrydc on 2017-04-22
Sorry for the late reply but I didn't know that there were answers.

Started with the easy suggestion, that is going to cups. Printing a test page resulted in nothing happening except for the usual notification that job is "held." BTW, the Location field is blank after I click on the printer listed in the cups page. Is that of any importance.

What happens with almost all print jobs is the HP printer program initially says "connected to localhost." Printer queue says "Held" when I try to print a file. But when printing doesn't happen, icon says "printer may not be connected to computer."

Other peculiarity:  HP prints when using its control panel.  So, when printing "Wireless Network Test Results" the page says "No problems found. Congratulations on the successful setup of your wireless printer."  But the last item under Current Configuration is "Internet --  Not Connected."  However, opening wireless program on the HP says I am connected.

If this is all besides the point, I'll try the Terminal route.

thank you for your efforts and would would appreciate further help.

---

### Post by jerrydc on 2017-04-24
BTW, don't know why my messages say I use Ubuntu 10.04.  I use 16.04 lts and always update when asked to.

Jerry

---

### Post by howefield on 2017-04-24
> **jerrydc said:**
> BTW, don't know why my messages say I use Ubuntu 10.04.  I use 16.04 lts and always update when asked to.

The signature that you choose to use on an internet forum isn't updated automatically just because you upgrade your operating system. You have to update it via your forums accounts profile.

Quick Links > Edit Profile > Edit Signature.

---

### Post by jerrydc on 2017-04-24
OK, here is a screenshot of what I got using the suggestion to go to terminal.

---

### Post by howefield on 2017-04-25
Appears that you dragged an image into your post and triggered a bug meaning your image came out as a load of junk base64 code.

Use the Reply to Thread button and click on the paperclip icon to attached your image to your posting, likely to have better results that way. :)

---

### Post by jerrydc on 2017-04-25
The only paperclip icon I see is Attachments and that opens File Upload Manager.  Don't understand what that is all about and do not have the time to learn how to use yet another program.  It was not simple, for example, to find Screenshot, get it to work and then incorrectly using it was too time consuming and frustrating an experience to want me to try to continue this particular line.

Perhaps it would be enough to say that using KenUBF's suggestion I came up with the identical wording he showed as a result of using 
[COLOR=#000000]lpc status all, except that my HP 5520 was listed.

When I used the next myfile command , I got "no such file or directory."

Jerry
[/COLOR]

---

