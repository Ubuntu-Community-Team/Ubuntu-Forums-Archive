---
title: "How does nautilus search for a file beginning with a &amp;amp;quot;.&amp;amp;quot; (dot)?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by bwallum on 2008-11-30
Hi

I have been trying to find all occurrences of a programme (googleearth as it happens) and remove them.

I used nautilus search and the search string googleearth. I searched the entire filesystem and I had hidden files showing.

I think I found everything but then later found .googleearth in my home directory.

How do I get nautilus to search for files beginning with a dot?

---

### Post by RATM_Owns on 2008-11-30
In /:
```
find / | grep googleearth
```

In ~
```
find $HOME | grep googleearth
```

---

### Post by bwallum on 2008-11-30
Hole in one! Thank you.

---

### Post by FreewheelinFrank on 2008-11-30
For future reference:

View>Show Hidden Files

---

### Post by o.besner on 2008-11-30
To see all hidden files you can simply do CTRL + H on your keyboard. Doing it again hides them. Useful for removing configuration files.

---

### Post by bwallum on 2008-12-02
Ok, found it, I did this

Go to Places>Search for Files 
In the 'Look in folder' drop down menu select 'File System'
Then use the 'Select more options' extension. Left click the triangle and in the drop down menu for 'Available options', left click on 'Show hidden and Backup files' then press Add. (The last bit, pressing Add, was where I lost contact with the nautilus designers)

Thank you for the prompt!

---

### Post by Jim Danner on 2008-12-06
> **bwallum said:**
> How do I get nautilus to search for files beginning with a dot?The answer to your original question is: *You can't.*

There are other solutions, most of them mentioned above: *find, locate, Places... Search,* but the most useful thing of all -- hitting the "search" button in your already-open Nautilus window -- doesn't find hidden files. (see also [this thread]("http://ubuntuforums.org/showthread.php?t=966685"))

So where you say "[SOLVED]" it is actually "[found a workaround and am sort-of satisfied with it]". :)

---

### Post by bwallum on 2008-12-06
If I do Places>Search for Files I am presented with a window called Search for Files. In that window I can Select more options, one of which is 'show hidden and backup files' (when an option is selected remember to 'Add' it).

I have attached a screenshot to show 'dot' files found during a search.

Once those options are selected they stick, so next time you do a search the options are automatically applied. I agree that no options are set with the default settings but it is a one off exercise to choose the options. 

That says solved to me, or am I missing something?

EDIT: ok you can't do it from File Browser and I agree that would be useful. Is 'Search for Files' nautilus? Is 'File Browser' nautilus? I'm not too sure of the difference to be honest, it all appears the same to me, so how about [half solved...I think...]

---

### Post by Jim Danner on 2008-12-10
> **bwallum said:**
> Is 'Search for Files' nautilus? Is 'File Browser' nautilus? I'm not too sure of the difference to be honest, it all appears the same to me, so how about [half solved...I think...]File browser = Nautilus. I agree, half solved. ;)

---

