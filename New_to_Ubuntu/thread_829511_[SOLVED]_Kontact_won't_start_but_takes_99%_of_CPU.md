---
title: "[SOLVED] Kontact won't start but takes 99% of CPU"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by mdsmedia on 2008-06-14
I've used Kontact as my PIM virtually since I started using Ubuntu, some 3 years ago.

Now, when I click on the shortcut in my panel, it won't open my PIM but does take up over 99% of my CPU.

I've considered uninstalling and reinstalling but fear losing my calendar and to-do data.

Any alternative would be appreciated.

Kontact starts on boot, that is it takes up all my CPU and I have to kill it. I can remove it from start on boot, but that will not fix the fact that I can't start my organiser.

---

### Post by freduardo on 2008-06-17
Try starting kontact from a terminal to see what errors it produces. This might help you determinating what the actual problem is.

---

### Post by mdsmedia on 2008-06-17
Thanks. After more than 2 days I searched elsewhere. Yes, I should and could have done that before, but didn't. I hoped I'd get a response here and when I didn't I searched Google... wasn't sure what I was looking for but different angles produced different results.

I came up with a number of pieces which vaguely got me somewhere.

In the end I had a corrupt file "std.ics".

I was able to open the file with gedit. I deleted a lot of entries and then reinstated the file. I've lost some data....not sure yet how much, but I've kept a backup of the original. I'm not sure where the corruption was, but I've got back a lot of data....once again, not sure how much.

Basically, what I did, was find the ".kde" folder in /home. I renamed it .kdetest (eventually .kdeoriginal).

I then restarted....logging out and logging in served the same purpose.

Doing so, the .kde folder recreated itself and was effectively empty....I restarted Kontact to no data.

I then copied everything over from .kdeoriginal to eliminate the corrupt file. That is...I gradually copied things over and restarted Kontact until something caused it not to start. 

I narrowed that down to the std.ics file...which unfortunately happens to hold all of the calendar and to-do data.

I despaired, until I read a post that said it was opened with Kate (which I believe is a KDE editor). I opened std.ics with gedit and went through, deleting entries which I didn't need....this is very subjective, but basically I was hoping to eliminate the corrupting entry.

At various stages I saved the file to my new .kde folder and tried opening Kontact. Eventually Kontact opened with no fuss. The problem now is adding back what isn't corrupt. As I said, I've saved the original, just in case.

I now have it working but I'm not yet sure what I've lost or whether I've got it all back, but I've got a lot of data back that I thought was lost.

---

