---
title: "[SOLVED] Firefox - Regarding history malfunction"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by CLomax on 2008-08-16
I have a problem with Firefox, it doesn't save any history, even though I set the preferences, which means that I can't use the back or forward button (pain in the bum).

I have managed to find the error console to try to put my finger on the problem. It links me to parts of a code which aren't working but I'm not exactly familiar with it.

BTW, if it's important, this started happening after attempting to install flash only to have it working if I tapped 'sudo firefox' into the terminal.

Here's an example of what I'm seeing

```
Error Console:
          PlacesUtils.history is undefined
Which links me to:
"PlacesUtils.history.queryStringToQueries(val, queries, { }, options);" which is highlighted.
```

Thanks in advance.

---

### Post by y-lee on 2008-08-16
This is probably a permissions problem from running firefox using sudo firefox. Always use gksudo firefox if you need to run firefox as root.

Now as how to fix it there is a hidden folder called .mozilla in your home directory. look in it and you should see a folder called firefox now open that folder and you should see a folder named xxx.default (assuming you only use firefoxes default profile) where xxx is a random looking string of characters. Now open the xxx.default folder and there should be a file called history.dat. Make sure you are the owner of this file and have read and write permissions for it. If not either change the permissions or delete the file. Note if root owns this file then moving it to the trash can will leave you with the problem of emptying the trash can, as emptying the trash can the usual way can not remove root owned files.

If this advice is not clear enough post back and we will help you thru the process. Good luck.

---

### Post by CLomax on 2008-08-16
Thank you very much for your reply; your advice was a great help. The solution you posted wasn't an exact solution but it helped me fix the problem.

For anyone who has this problem, uninstall firefox with synaptic, delete the hidden .mozilla folder in /home/ then reinstall firefox. If you want to keep your history backup the history.dat file and replace it once you have finished reinstalling.

---

