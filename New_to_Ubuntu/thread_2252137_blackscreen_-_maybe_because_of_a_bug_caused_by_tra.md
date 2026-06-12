---
title: "blackscreen - maybe because of a bug caused by trashbin?"
date: 2014-11-09
forum: New to Ubuntu
---

### Post by mimi2 on 2014-11-09
Hello,

I have a problem and dont seem to be able to find the solution. i am quite new to ubuntu and didnt have any real problems yet. 
today I tried emptying my trashbin. it did not work - the icons remained in the folder. beause the folder did not react after several times of trying this I restarted my computer. Now when I start ubuntu first the purple page with the logo appears and afterwards there is a blacksreen. I have a dualsystem with windows. windows does not seem to have a problem. i tried starting  in the grub menu something that is in my understanding an earlier version of my ubuntu but the blacksreen appeared again.
Beause I dont want to break anything I did not dare to do anything in the recovery mode because I dont have a deeper understanding of what i would be doing there.
I have looked at blakscreensolution threads but did not see a solution for my problem there.

Thanks for any help!

---

### Post by llamabr on 2014-11-09
What method did you use to clear your trashbin? I'm afraid that probably you deleted something important.  If you're brand new, and you don't have much data stored on your ubuntu partition, you might take this early opportunity to re-install.  It may be faster than trying to troubleshoot what you deleted.

---

### Post by mimi2 on 2014-11-10
Thak you for answering,
I opened the trashbin window and pushed the button to empty the trashbin - I dont know what could have possibly gone wrong there.
 of course I could just reinstall ubuntu as last solution but i would really like to try solving the problem first...
is there no way of finding the cause of this blacksreen?

---

### Post by Impavidus on 2014-11-10
Do you have any idea what was in that trash can?

You should be able to boot from a live disk. Then open the file manager and click in the left pane on the partition of your installed system. Enable showing hidden files and navigate to the directory /home/your-user-name/.config/share/Trash. There you will find your trash can. [s]Maybe you can empty it with root permissions.[/s] Don't try to empty it right now. First check what's inside. It could also be some sort of file system damage. Run a file system check from the live disk. That never harms.

You could do both actions from recovery mode too, but I think you won't like the text-only interface.

I agree that if you have no clue what went wrong reinstalling is often the fastest way out, but usually not the most educational way out.

---

### Post by grahammechanical on 2014-11-10
> [COLOR=#000000]I'm afraid that probably you deleted something important. [/COLOR]

That gets my vote. We remove something to the Rubbish Bin and then delete what is in the Trash Can and then reboot and the system is broken. It is possible that you put system files into Trash but the normal use of the action to empty the Trash Can command does not have permission to delete those files. So, the action does not proceed. But by moving those files to the Trash Can we have removed them from their correct location. Then a reboot ends up with a broken system.

Because the empty trash can operation failed you should be able to restore the files using the method already suggested.

Regards.

---

### Post by mimi2 on 2014-11-10
ok, thank you for the answers!
I would like to do it in recovery mode with the text interface, but maybe that would be too complicated for now. First I will try to do it by using a live disk as you suggested.

regards

---

