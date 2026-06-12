---
title: "Bin"
date: 2010-12-18
forum: Programming Talk
---

### Post by el_diablo on 2010-12-18
Hi.....
Can anyone plz tell how to look bin files

---

### Post by Wistful on 2010-12-18
Rephrase your question, its not very clear what do you really mean?!

A 'bin' file is typically the extension given to a binary executable. Either change permissions to execute it:

# chmod +x filename.bin
# ./filename.bin

or use a shell interpreter to run it:

# sh ./filename.bin

Also read [Command to run (execute) bin files in Linux]("http://www.cyberciti.biz/faq/howto-unix-command-run-execute-bin-files-in-linux/") and [Before You Ask]("http://www.catb.org/~esr/faqs/smart-questions.html#before")

---

### Post by roccivic on 2010-12-18
If what you want is to _view_ binary files, then you might want to try a hex editor such as ghex.

```
sudo apt-get install ghex
```

---

### Post by SevenMachines on 2010-12-19
Generally i'd say 'objdump' is a good place to start, it comes with binutils unsurprisingly, and has plenty of options for getting info or disassembling object files.

---

### Post by Vox754 on 2010-12-19
> **el_diablo said:**
> Hi.....
Can anyone plz tell how to look bin files

I hope you are not affiliated with the diablo himself.

But your question makes absolutely no sense. Please ask a better question.

What do you want to do?
What file are you trying to run?
Where did you get this file?
What tutorial are you following?
Are you trying to disassemble a binary file?
Are you trying to look at the source code of a binary file?
How is this related to programming?

Answer some or all of these questions, and provide better information, in order to get better help.

---

