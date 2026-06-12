---
title: "Stuffkeeper - The different way to catalog stuff"
date: 2008-04-03
forum: Programming Talk
---

### Post by Rasi on 2008-04-03
Hi there, this is not my own Project, i just help testing it, but as its in a very usable state i though to spread the word.

You probably know apps like WhereIsIt, Tellico and others. Stuffkeepers goes a compareable direction, but with one major difference: It is not bound to any pre-defined types of things you want to catalogise.

This is why the program might look very empty on 1st start, as you will have to create a type (e.g. Audio CD).
You define what this type should consist of and have several options to do so. (Strings, lists, textfields, sliders, checkboxes, images, Integer, Date & Time, Link)
You will see what those fields do, once you used them one time (Or check out the Beginners Guide on the webpage)
You can set up as many types with as many entries as you want.

Furthermore Stuffkeeper lets you define tags, which can be associated with every Database entry that is present. This helps to find things easily alot and combined with the filter, that lets you search for specific fieldnames/content you should have your desired results very fast.

Another feature is the possibility to export the database (or parts of it). At the moment it can only output css and html, but using a general template should make it easily output to anything else too.
Plugin support is also planned, but not sure when this will be done.

The program is using sqlite3 as a backend and is pretty fast. Altho its titled pre-alpha at the moment, it runs fairly stable on my machine.


*edit*

webpage: [www.stuffkeeper.org](www.stuffkeeper.org)


and join us on #stuffkeeper on the network you are on anyway

To make suggestions and or reports bug, here is the bugtracker located: [http://bugtracker.sarine.nl](http://bugtracker.sarine.nl)

---

### Post by qball on 2008-04-06
First package, so no idea how well it works:

[https://launchpad.net/~qball-qballcow/+archive](https://launchpad.net/~qball-qballcow/+archive)

---

### Post by Bou on 2008-04-09
I'll be keeping a close eye on this :D

---

### Post by Rasi on 2008-04-21
Update:

New webpage: [www.stuffkeeper.org](www.stuffkeeper.org)

- Added ability to split Views:
- New Type Editor
- Many small fixes and cleanups...

[http://stuffkeeper.org/index.php/DevNews](http://stuffkeeper.org/index.php/DevNews)

---

### Post by Rasi on 2008-04-27
> After some longer time, a new fancy test-release. This release is the last release before the release with major feature changes to the core of the program. This release however includes many, many additions: 
Working translation support, including a German translation.
Generated title support. You can now have the title of an item build up from fields in the item. 
Improved item layout, you can now pack fields in a horizontal/vertical box and nest these. This includes a basic layout viewer.
Locking of the interface. This protects you from making accidental edits.
Basic Plugin support. This is very early stage, so plugin api is not stable yet. 
Framework for installing a few basic types on first-run. 

It fixes the following things: 
Plugged several memory leaks. 
Fixed incorrect rebuilds, by moving to autotools instead of waf. 
Speedups, stuffkeeper starts in less then a second with 3500 items. 
Several usability fixes in Data list. 
Remove blue color from data-link, as it breaks dark themes. 
Fix text color when editing an item and the edit color shows. 
lot off small things.

get it here: [http://download.sarine.nl/Programs/StuffKeeper/stuffkeeper-0.10.0.tar.gz](http://download.sarine.nl/Programs/StuffKeeper/stuffkeeper-0.10.0.tar.gz)

---

### Post by qball on 2008-04-28
> **Rasi said:**
> get it here: [http://download.sarine.nl/Programs/StuffKeeper/stuffkeeper-0.10.0.tar.gz](http://download.sarine.nl/Programs/StuffKeeper/stuffkeeper-0.10.0.tar.gz)

Or get it from my ppa. [https://launchpad.net/~qball-qballcow/+archive](https://launchpad.net/~qball-qballcow/+archive)

---

### Post by kung fu buntu on 2008-05-10
This is very interesting. I'll have to try it, since I've been looking for a replacemente for whereisit for a long time.
Well, actually I've only search for a replacement 2 months ago, but I've been stuck for 2 years now.
And it would be nice if the replacement would be something better than whereisit which would also allow me to replace some lists in txt files (e.g. for games or movies).

This replacement search led me to track down existing tools and try many of them.
I even made a thread: ["Cataloging software (list included, critic needed)"]("http://ubuntuforums.org/showthread.php?t=726902") with the hope of getting some feedback.

I would ask you Rasi or even Stuffkeeper's coders to comment on my thread, since it has some interesting questions on the 3rd post (especially number 11).

I also strongly suggest people to try Datacrow since it's also very flexible and already includes lots of pre-defined collections.

---

### Post by Rasi on 2008-05-18
Finally an update:

> This is a great day for Stuffkeeper! Took a while, but now you can finally enter your Audio CD's in no time at all! Just chose "Tools -> Musicbrainz" to search for a query and its in your database! And as videos say more than words: [http://random.sarine.nl/stuffkeeper-musicbrainz-plugin.ogv](http://random.sarine.nl/stuffkeeper-musicbrainz-plugin.ogv) 

The Plugin is not in Stuffkeepers main branch yet tho. For the brave ones: git clone git://git.sarine.nl/stuffkeeper-musicbrainz.git

Also keep in mind: This is concidered a proof-of-concept plugin, so others can see how it works - or in other words: You want a service to be added? Code it! :)

---

### Post by pt123 on 2008-05-25
Would stuff keeper ever have the ability to scan a disk and add the files into a catalog, or is that not in the scope of the application.

---

### Post by Can+~ on 2008-05-25
I would make two suggestions to your project.

You compare the application to some others, that it can hold certain type of data; but still, I don't get what this thing does. I mean, if you want to sell your product (as a metaphor), at least tell me what it does, why I should use it, what features does it have.

Second, the name "StuffKeeper". Uhm. It's better than other names I've seen out there, but still it's not very descriptive. I would suggest names, but I still don't know what this is about.

Seeing the application (your screenshots), looks great, but I usually don't download things until I know what they do, so I can't give a better opinion.

---

### Post by qball on 2008-05-30
> **Can+~ said:**
> I would make two suggestions to your project.

You compare the application to some others, that it can hold certain type of data; but still, I don't get what this thing does. I mean, if you want to sell your product (as a metaphor), at least tell me what it does, why I should use it, what features does it have.

Second, the name "StuffKeeper". Uhm. It's better than other names I've seen out there, but still it's not very descriptive. I would suggest names, but I still don't know what this is about.

Seeing the application (your screenshots), looks great, but I usually don't download things until I know what they do, so I can't give a better opinion.


I am terrible with program names. I picked stuffkeeper because it was not yet taken, and somewhat descriptive. 

I agree a better story should be told on what it does. Problem is, it tries to be flexible, making it a harder story to tell.
Basic:
Stuffkeeper is a program that can catalog your inventory, any inventory.

---

### Post by qball on 2008-05-30
> **pt123 said:**
> Would stuff keeper ever have the ability to scan a disk and add the files into a catalog, or is that not in the scope of the application.

I don't think stuffkeeper is the most suited application for this job. But writing a plugin, it _is_ possible.

---

### Post by Rasi on 2008-06-19
Hmm personally i think Stuffkeeper is the perfect name for it... The application keeps an archive of Stuff that you own.. whatever it is...

anyway - new release!

> 
Because a very very busy time this release is later then I planned it, but it is here now. Enjoy. 

Added features: 
For debugging you can now get more info about timing, how long it took to load the db, load the items, etc. 
Shadow and border around the images. 
Images smaller then the maximum image size are no longer scaled up. 
Allow dragging and dropping images from any (gio supported) location. With progress bar and cancel button. 
New date widget. The widget no longer supports time, it does however support "no date" and obeys localization. Also allows for custom markup. 

Bug fixes: 
Improved plugin api. 
Icon support. 
Fallback functions implemented. 
Cleaned up the public api used by plugins. 
Make the internal dependencies correct. 
Don't force plugins to compile against sqlite for the sqlHandle. 
Hide internal functions. 
Added README and INSTALL file. 
Localization on the date field. 
Show image preview in the file-chooser. 
Add file-filters to the file-chooser. 
Code Cleanups. 
More Code Cleanups.

get it: [http://download.sarine.nl/Programs/StuffKeeper/stuffkeeper-0.11.0.tar.gz](http://download.sarine.nl/Programs/StuffKeeper/stuffkeeper-0.11.0.tar.gz)

---

