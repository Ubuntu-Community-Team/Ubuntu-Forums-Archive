---
title: "VT_handler defect in 10_linux"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by Randy_Bass on 2013-08-06
I have a dual boot system with Windows XP. My disk was corrupted by a virus in XP. I was able to recover XP, but had to reinstall Ubuntu 13.04. I'm trying to customize the Grub 2 file, I added a custom entry and made changes to 05_debian_theme. I run update-grub, but get an error message. In the grub.cfg file, the block of code with the error is:

function gfxmode {
               set gfxpayload="${1}"
               if [ "${1}" = "keep"  ];  then
                      set vt_handoff=vt.handoff=7
               else
                      set vt_handoff=
               fi
}

CLearly, the vt_handoff line after the else statement is an incomplete statement. I traced this down to the file 10_linux. 
I tried to do some research on this to find what the assignment should be, but couldn't find anything. I tried fixing it by copying the line before the else statement, making the 2 lines identical, but even with that I go an error when I ran update-grub. I'm surprised I have a defective file, as I'm sure others are able to rebuild their grub files okay.

---

### Post by Azdour on 2013-08-06
Hi,

I've checked my grub.cfg and I have the same code as you have.  I'm guessing that set vt_handoff= makes the variable empty.

I'm wondering if it is your custom entry that is causing the problem?  If you revert your custom entry does the grub rebuild?

---

### Post by matt_symes on 2013-08-06
Hi

Why don't you post the entire error message displayed after updating grub and the files you have changed.

Kind regards

---

### Post by Randy_Bass on 2013-08-06
Thanks AZ. That gives me a little more confidence, but don't understand why I'm getting the error msg. But I also had 6 system crashes in 7 hours yesterday. I'm thinking of reverting back to 12.10 or even 12.04.

Matt, The full error messagefollowing update-grub is:
error: syntax error.
error: incorrect command.
error: syntax error
Syntax error at line 101
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* or please file a bug report with
/boot/grub//grub.cfg.new file attached.done

AZ,

I went into my custom entry file and commented out every line, and then did an update-grub, and it compiled fine. Don't understand the issue with line 101 in the config, but it seemed to be the innocent victim here. I'll look at my custom entry more carefully. Thanks.

AZ,

I have a habit of having my open and close brackets in the same column for readability. I moved the open bracket to the end of the menuentry line and then the up-date-grub worked without issues. SO now I'm ready to reboot and see if that worked. Too bad the updater can't be a little smarter about the source of errors. Thanks.

---

