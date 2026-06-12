---
title: "Clear Recent files list"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-08-16
I wish to remove the recent files list on Ubuntu (kylin) that i installed on one of my friend's comp. 
I tried this method :
[B]rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace[/B]
but it did not work.
Then i deleted  **recently-used.xbel**  file
still it did not work.
Then i installed Activity log manager but it does not starts.
What should i do to Clear the list of recently used files.

I would also like to know how i can remove (forget permanently) the details of my wifi connection.

---

### Post by stinkeye on 2013-08-16
To clear immediately run....
echo > ~/.local/share/recently-used.xbel

See this thread. [http://ubuntuforums.org/showthread.php?t=2154627](http://ubuntuforums.org/showthread.php?t=2154627)

---

### Post by 3dmatrix on 2013-08-16
> **stinkeye said:**
> To clear immediately run....
echo > ~/.local/share/recently-used.xbel

See this thread. [http://ubuntuforums.org/showthread.php?t=2154627](http://ubuntuforums.org/showthread.php?t=2154627)

It did not work that way. Even deleting the file did not work. I had to go to settings and clear history.

---

### Post by stinkeye on 2013-08-16
Running
```
echo > ~/.local/share/recently-used.xbel
```
should clear the recently used list shown in apps like gedit and nautilus.

Using activity log manager(privacy) to delete history
or
Removing **~/.local/share/zeitgeist/activity.sqlite** should remove 
recent activity from the dash, after a log out.

---

### Post by 3dmatrix on 2013-08-16
> **stinkeye said:**
> Running
```
echo > ~/.local/share/recently-used.xbel
```
should clear the recently used list shown in apps like gedit and nautilus.

Using activity log manager(privacy) to delete history
or
Removing **~/.local/share/zeitgeist/activity.sqlite** should remove 
recent activity from the dash, after a log out.

As I mentioned earlier, non of these worked.

---

### Post by stinkeye on 2013-08-16
> **3dmatrix said:**
> As I mentioned earlier, non of these worked.

I'm on 13.04 so can't test for 12.04. Maybe it's different. :-?

---

### Post by 3dmatrix on 2013-08-16
> **stinkeye said:**
> Running
```
echo > ~/.local/share/recently-used.xbel
```
should clear the recently used list shown in apps like gedit and nautilus.

Using activity log manager(privacy) to delete history
or
Removing **~/.local/share/zeitgeist/activity.sqlite** should remove 
recent activity from the dash, after a log out.

As I mentioned earlier, non of these worked.

---

### Post by 3dmatrix on 2013-08-17
> **stinkeye said:**
> I'm on 13.04 so can't test for 12.04. Maybe it's different. :-?


This problem is in 13.04

---

### Post by stinkeye on 2013-08-18
> **3dmatrix said:**
> This problem is in 13.04
Well all I can say is t works here in ubuntu 13.04.
Can't test in Kylin.

---

