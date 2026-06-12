---
title: "[SOLVED] HPLIP Printer Permission Problem"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by ubv1308 on 2008-10-21
Ok, I have an HP LaserJet 1018 and I just installed the latest hplip version. I did it through hplip-2.8.9.run on my desktop.

It asked me a couple question, installed stuff and ask me to restart.

Now, I'm stuck with a folder on my desktop that I can't even open "hplip-2.8.9.", all printer options are gone from the system menu and the only thing related in the menu is HP Device manager which doesn't react when I click on it.

I installed hplip because ubuntu had recognize the printer, the task was being sent but the printing was not happening and I had read this could fix the problem. Now I'm in a bigger mess.

---

### Post by fballem on 2008-10-21
Three questions:

1. Did you uninstall the old version of hplip through synaptic first?
2. If you right-click on the folder on your Desktop and look at the permissions, who 'owns' the file?
3. When you installed, did you type ```
sudo sh hplip-2.8.9.run
``` or just ```
sh hplip-2.8.9.run
```? The correct answer, hopefully, is the second choice, not the first one.

---

### Post by ubv1308 on 2008-10-21
1.Nope
2.root
3.I think sudo sh . I know I try just sh first before learning to go to the the desktop through cd but when I did it, I think I used the sudo sh command instead.

---

### Post by fballem on 2008-10-21
> **ubv1308 said:**
> 1.Nope
2.root
3.I think sudo sh . I know I try just sh first before learning to go to the the desktop through cd but when I did it, I think I used the sudo sh command instead.

That's why you can't delete the folder normally. Please make a note of the name of the folder.

VERY CAREFULLY:

Open a Terminal. Run the following commands:
```
cd ~/Desktop
dir
```
Please check the list to make sure that the folder is there.
```

sudo chown -R username:username foldername

```
where folder name is the actual name of the folder, and username is your actual username.

close the terminal.

Assuming that all went well, you should be able to right-click on the folder, check properties, and you should now be the owner. If that's correct. then you can now delete the folder.

Once that's done, you may be able to re-run the original installation. Please do not use sudo to run it. It will ask you for your password as part of the installation process.

If that is not successful, then I'll have to do some serious digging to find out how to get rid of the old installation.

Please let me know how you do,

---

### Post by ubv1308 on 2008-10-21
It work !

The command did the trick, I deleted the folder and reinstalled through the sh command. Everything is working now, I can print fine.

What do I do with the hplip-2.8.9 folder on my desktop now ? Is it like an unzip/temp from the run program that I can now delete or do I have to actually let it there (can I move it?). If I have to let it there, any way to "hide it" and bring it out through ctrl-h ?

Thank you very much fballem, the help was really appreciated.

PS : Can I edit my title to add the [SOLVED] bracket or will a mod do it ?

---

### Post by fballem on 2008-10-21
> **ubv1308 said:**
> It work !

The command did the trick, I deleted the folder and reinstalled through the sh command. Everything is working now, I can print fine.

What do I do with the hplip-2.8.9 folder on my desktop now ? Is it like an unzip/temp from the run program that I can now delete or do I have to actually let it there (can I move it?). If I have to let it there, any way to "hide it" and bring it out through ctrl-h ?

Thank you very much fballem, the help was really appreciated.

PS : Can I edit my title to add the [SOLVED] bracket or will a mod do it ?

1. You're welcome
2. You can delete the file (and the folder) from your desktop. You don't need to retain these at all.
3. If you look at the top of the screen, you will see "Thread Tools". If you select that, you can  mark the thread solved.

Regards,

---

