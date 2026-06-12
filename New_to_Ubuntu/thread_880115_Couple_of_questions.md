---
title: "Couple of questions"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Harpz on 2008-08-04
Hi all

Changed from Vista to Ubuntu 4 days ago and haven't looked back (tired of the Vista donkey). Haven't got a clue what I'm doing some times but have got what I've needed to get done. 

All my hardware installed first time, this never happened with Vista. I have made myself a nice conky and customized my desktop, and have been able to almost everything that i could do with Vista (just have to get used to or find a new way of doing things). 

Couple of small question's though (sure there will be many more later)

1. Is there a way make the Nautilus File Browser display "View as List" as default whenever i open any window as at the moment i have to keep changing from "View As Icons"

2. I often extract lager numbers of files from rar achieves, to do this I used to use ExtractNow [http://www.extractnow.com/](http://www.extractnow.com/) I know i can use Wine and have installed ExtractNow with Wine. Is there a way to extract alot of achieves within Ubuntu?

Thanks it for now hope some one can help.
Mike

---

### Post by northern lights on 2008-08-04
1. In nautilus, navigate to "Edit > Preferences". First Option is "Default View".

2.```
sudo apt-get update && sudo apt get install unrar
```
For split archives run```
unrar -e filename.001
```If the rest is named filename.002, filename.003, etc then it'll detect the rest.

---

### Post by Harpz on 2008-08-04
> **northern lights said:**
> 1. In nautilus, navigate to "Edit > Preferences". First Option is "Default View".

2.```
sudo apt-get update && sudo apt get install unrar
```
For split archives run```
unrar -e filename.001
```If the rest is named filename.002, filename.003, etc then it'll detect the rest.

Thanks for the reply
Will that method of extracting allow me to unrar from multiple directories?

Say a given directory has 6 subfolders in it and each of these folders has a rar set in it, is there any easy way to tell it to go in to directores 1-6 and extract the files from the rar sets in them?

With ExtractNow i just drag the folders to its window it scans the folders and lists what can be extracted and then i just tell it to extract all the files to a give directory.

Mike

---

### Post by northern lights on 2008-08-04
> **Icerat said:**
> With ExtractNow i just drag the folders to its window it scans the folders and lists what can be extracted and then i just tell it to extract all the files to a give directory.
Oh, like that.
Off my head I dunno an app capable of that. I'm sure a script will do. I'll post one tomorrow morning.

---

### Post by mcduck on 2008-08-05
Also note that you don't need to use command line to extract .rar archives. After you have unrar installed you can just right-click them and select "extract here". ;)

---

### Post by lisati on 2008-08-05
> **Icerat said:**
> 
1. Is there a way make the Nautilus File Browser display "View as List" as default whenever i open any window as at the moment i have to keep changing from "View As Icons"

Try the "view" option then "view as list" - it should remember the setting when you close the browser.

---

### Post by roquefilipe on 2008-08-05
unrar has a switch to recurse subdirectories: "-r"

use "man unrar" in the command line to obtain more information about unrar. 

But the best would be to use open formats :)

---

### Post by hyper_ch on 2008-08-05
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by Harpz on 2008-08-19
> **northern lights said:**
> Oh, like that.
Off my head I dunno an app capable of that. I'm sure a script will do. I'll post one tomorrow morning.

Any idea when i can look at script m8?

---

