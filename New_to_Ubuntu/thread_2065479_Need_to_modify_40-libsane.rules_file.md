---
title: "Need to modify 40-libsane.rules file"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by tomhsien on 2012-10-02
Hi all,

I am trying to get my Brother MFC-8690DW printer to work, specifically the scanner.
I am following the instructions on this page: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

It says to open "/lib/udev/rules.d/40-libsane.rules" and add the lines:

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

So I clicked around, found and opened that file with gedit, added the line, but I am unable to save it.

I am not familiar with the command line, and am unsure what to do.  I am using Ubuntu 12.04.  Can someone show me how to open that file with the proper permission to edit it?

Thanks in advance.

P.S. - In your instructions, please treat me like an idiot.  I am pretty clueless.

---

### Post by tomhsien on 2012-10-02
Hehehe,

OK.  I figured it out.
Just go to the command line and do:

sudo gedit.

Boy, do I feel silly.

---

### Post by pdc on 2012-10-02
we all learn new things with linux every day;

hope you got it all working

this thread

[http://ubuntuforums.org/showthread.php?t=2065627&highlight=brother+printer](http://ubuntuforums.org/showthread.php?t=2065627&highlight=brother+printer)

has very similar issues; sounds like it got resolved too

---

