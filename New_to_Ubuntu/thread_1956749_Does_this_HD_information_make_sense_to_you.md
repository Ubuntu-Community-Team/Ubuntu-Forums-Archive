---
title: "Does this HD information make sense to you?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-11
[http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=hdfullquestion.jpg](http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=hdfullquestion.jpg)

On boot I get HD0 full error?

---

### Post by idoitprone on 2012-04-11
> **Boyntonstu said:**
> [http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=hdfullquestion.jpg](http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=hdfullquestion.jpg)

On boot I get HD0 full error?

yes it make sense your other two pictures have knife and your ready to slice delicious bread. Dawm, I am jealous

Other than that, it just a mundane disk usage program that doesnt have must meaning

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

please run this boot info script on live cd to give us a better understanding

Directions is in the link

---

### Post by oldfred on 2012-04-11
I am not sure but I think that is just saying of your 100% disk 41% is used.

Post these:
 df -i
df -Th | sort

---

### Post by Boyntonstu on 2012-04-11
> **oldfred said:**
> I am not sure but I think that is just saying of your 100% disk 41% is used.

Post these:
 df -i
df -Th | sort

[http://i348.photobucket.com/albums/q339/BoyntonStu/df-121112.jpg](http://i348.photobucket.com/albums/q339/BoyntonStu/df-121112.jpg)

[http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=df-121112.jpg](http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=df-121112.jpg)

Images captured from screen using KSnapshot

---

### Post by oldfred on 2012-04-11
I do not see any issue?

It is also easier if you just copy & paste code or results from the termial into your message. If longer use code tags, or highlight like you would when copying and click on the # in the edit panel above your message.

If a screen shot from a gui app you can upload the .png using the paperclip icon in the message panel.

---

### Post by anewguy on 2012-04-11
> **Boyntonstu said:**
> [http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=hdfullquestion.jpg](http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=hdfullquestion.jpg)

On boot I get HD0 full error?

After reading this thread and looking at the various pictures, I have to ask:

do you get some sort of error message at boot time saying HD0 is full?  If so, post that.

If you are going by what says 100% in your attached image, as others have stated it just shows your disk size THEN shows the amount used - only 42%.  You still have 58% of that drive open, and your drive it's a lot of space.

Dave ;)

---

