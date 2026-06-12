---
title: "'Pictures' folder"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by Don Cox on 2012-01-19
In my Home folder there is a Pictures folder. This is listed in the 'Tree' view of the sidebar but not in the 'Places' view.

What is the explanation for this and how can 'Pictures be made to appear in the 'Places' view?

Ubuntu 11.10  Nautilus 3.2.1

-- 
Don Cox

---

### Post by cortman on 2012-01-19
Boookmarks> Edit Bookmarks.

---

### Post by Don Cox on 2012-01-19
> **cortman said:**
> Boookmarks> Edit Bookmarks.

That does not work; if the answer were as simple as that I would not be asking the question.

---

### Post by Rex Bouwense on 2012-01-19
You cannot drag and drop?

---

### Post by Don Cox on 2012-01-19
> **Rex Bouwense said:**
> You cannot drag and drop?

I can drag but cannot drop!

---

### Post by Paddy Landau on 2012-01-19
Don, I think you have to give us some more information. Pictures is there by default, so something has happened to take it away from you.

You say drag-and-drop does not work. Please be specific: what precisely happens when you try? If you edit your bookmarks, is it perhaps listed there but disabled?

---

### Post by Don Cox on 2012-01-19
Paddy, like you I am sure Pictures has been accidentally removed.

The icon flies back to the Home folder when attempt to drop it anywhere in the sidebar.

It is possible to put Pictures into the Bookmarks area using Bookmarks Edit but not possible to place it under Computer where it should be. Tree view of the sidebar, I reiterate, is Okay

---

### Post by cortman on 2012-01-19
> **Don Cox said:**
> Paddy, like you I am sure Pictures has been accidentally removed.

The icon flies back to the Home folder when attempt to drop it anywhere in the sidebar.

It is possible to put Pictures into the Bookmarks area using Bookmarks Edit but not possible to place it under Computer where it should be. Tree view of the sidebar, I reiterate, is Okay

Sorry if my answer was too basic- like you said, it'd be a quick fix, but probably not fix what ultimately seems to be wrong with nautilus.

Unless the others have better ideas, you could always try removing and reinstalling nautilus.

---

### Post by Paddy Landau on 2012-01-19
> **Don Cox said:**
> ... not possible to place it under Computer where it should be.
Mine isn't under Computer. In fact, I don't have a Computer.

I have a group of default icons that I cannot change (home folder, Desktop, File System and more), then a separator, then a group of icons (some of which were default) that I can change.

I wonder why yours and mine are so different?

---

### Post by Don Cox on 2012-01-19
> **Paddy Landau said:**
> 

I wonder why yours and mine are so different?

At a guess, because you're using 11.04 and I'm using 11.10

-- 
Don

---

### Post by mcduck on 2012-01-19
> **Don Cox said:**
> In my Home folder there is a Pictures folder. This is listed in the 'Tree' view of the sidebar but not in the 'Places' view.

What is the explanation for this and how can 'Pictures be made to appear in the 'Places' view?

Ubuntu 11.10  Nautilus 3.2.1

-- 
Don Cox

If you have at any point (accidentally or on purpose) removed the Pictures folder, the config that links it as the Pictures location for your user, gives it a specific icon in the file manager and adds it to Places would have been removed.

Anyway, it should be a simple thing to fix. Open the *~/.config/user-dirs.dirs* -file in a text editor, and make sure it contains the following line:
```
XDG_PICTURES_DIR="$HOME/Pictures"
```

...you might have to log out and back again before the change takes effect.

---

### Post by Don Cox on 2012-01-19
> **mcduck said:**
> If you have at any point (accidentally or on purpose) removed the Pictures folder, the config that links it as the Pictures location for your user, gives it a specific icon in the file manager and adds it to Places would have been removed.

Anyway, it should be a simple thing to fix. Open the *~/.config/user-dirs.dirs* -file in a text editor, and make sure it contains the following line:
```
XDG_PICTURES_DIR="$HOME/Pictures"
```

...you might have to log out and back again before the change takes effect.


Absolutely 100% correct. The word Pictures was missing!
Please accept my most sincere thanks.

-- 
Don Cox

---

### Post by Paddy Landau on 2012-01-19
Whew! I'm glad McDuck had the answer, because I was baffled.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Don Cox on 2012-01-19
> **Paddy Landau said:**
> Whew! I'm glad McDuck had the answer, because I was baffled.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Done; thanks for your help.

---

