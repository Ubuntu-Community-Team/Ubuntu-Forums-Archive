---
title: "Make Ktorrent default on Firefox"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by held7over on 2013-10-10
Ubuntu 12.04

I have several computers of my own running 12.04 and _Firefox automatically calls Ktorrent when I click on a .torrent file_, however, I am setting up a friend's computer to use Ubuntu 12.04...and his computer doesn't have copies of my own personal configuration files which evidently carry forward this ability for my own computers as I install new versions of Ubuntu.....and I seem to have forgotten how this is done or something has changed dramatically! 

This is his first experience with Linux and I can't seem to get his firefox browser to do the same automatic action!   I have been googling for an answer, but everything I find has directions that seem to be far outdated and no longer applicable. 

What do I need to do to make his Firefox browser automatically hand a .torrent file to Ktorrent???

Thanks for your thoughts and suggestions! :)

---

### Post by SeijiSensei on 2013-10-10
First, have you installed ktorrent?  As a KDE application, I don't believe it is part of the stock Ubuntu distribution.  Once you have done so, click on a torrent link.  That should bring up the Firefox dialog that lets you select an application. Now pick "other" from the drop-down box then navigate to /usr/bin and pick ktorrent.

---

### Post by held7over on 2013-10-10
I forgot to add that I had Firefox download a .torrent file, then using Nautilus, I opened the .torrent file's properties, and selected Ktorrent as it's default application. So, while I can now double click on the .torrent file and it automatically call Ktorrent, Firefox still doesn't hand it automatically to Ktorrent.......so.....there must be something else I need to do....

---

### Post by held7over on 2013-10-10
Hi SeijiSensei! Thanks for your reply.

Yes. I have ktorrent installed. The problem is, when I click on downloading a .torrent file, Firefox's popup window only offers "Cancel" and "Save", there is no "Other" button choice showing!. Weird! 

I haven't figured out how to get it to offer me the option of associating an application of my choice for .torrent files! It just wants to save the file to disk somewhere....

---

### Post by SeijiSensei on 2013-10-10
I've never seen the Firefox dialogue not include an "Open" entry with a drop-down next to it.

However, another route is to use Edit > Preferences > Applications and see if something is assigned to handle torrent files.  If so, you can choose the default application from the associated drop-down menu.  If there is no entry for torrents, then you should have gotten the Open dialog where you can specify the default program.

---

### Post by held7over on 2013-10-10
Yeah. That was the second thing I tried (and just re-checked again), was going to Edit > Preferences > Applications and looking for something concerning Torrent files. I didn't find anything there on his system which is setting here in my computer room. So, I checked my own computer's firefox Edit > Preferences > Applications and found that I had a "BitTorrent seed file" in my list that was marked as "Always Ask"! 

I tried researching how to add that entry, but have had no luck on finding directions for doing that either!

But, I can tell you that his list of instances allowable in Edit > Preferences > Applications is about half or less than my own computers show....something doesn't seem to be picking up the entries that need to be there.

What do you think???

---

### Post by held7over on 2013-10-10
In fact, looking at the "Content Types" listed on his machine at Edit > Preferences > Applications  the listing jumps from the A's  (AXV/file) to the I's (irc) with nothing in between those two Content Types. It's like a chunk of Content Types just aren't there....and no apparent way to get them there....although, I should think that they would appear when FireFox encounters one that is being clicked upon!!!

---

### Post by ajgreeny on 2013-10-10
If you click in the "Always ask" you should get a dropdown box with several options.  On my machine I have transmission as an option as it is the only torrent client installed.  If ktorrent is not in your list you should be able to add it by using the "Use other" option and navigating to ktorrent (in /usr/bin if necessary).

See my screenshot which may help show what I'm talking about.

---

### Post by held7over on 2013-10-10
Thanks for your input ajgreeny.  However, what you are suggesting is the second thing I tried, but the list of Content Types in the Applications tab, does not include a "BitTorrent seed file" entry like your does! So, there is no corresponding drop down menu to the left of it to make the selection we both want me to select. Instead, his content list jumps from the "AVI video" Content Type to the "irc" Content Type, which means, everything between those two alphabetically listed types is missing!  For some reason, Firefox is not adding a BitTorrent selection when the browser is used to click upon a .torrent file. SO, all it offers me is to SAVE the File or CANCEL the opperation.

I just finished completely removing Firefox and also deleted the .mozilla hidden file in his home directory and reinstalled it all. The same problem still exists. 

It would be nice if we knew the name and location of the config file we are seeing in this Applications List, I could just edit in what is needed manually....I wonder if anyone knows where it is at and if it is editable?

---

### Post by heir4c on 2013-10-10
Edit: See first a later post of held7over in this tread!!!:  [http://ubuntuforums.org/showthread.php?t=2179932&page=2&p=12813187#post12813187](http://ubuntuforums.org/showthread.php?t=2179932&page=2&p=12813187#post12813187)


(I find something:
[http://ubuntuguide.org/wiki/KTorrent](http://ubuntuguide.org/wiki/KTorrent))

---

### Post by oldos2er on 2013-10-10
According to Firefox's help, if you delete the file /home/user/.mozilla/firefox/*.default/mimeTypes.rdf it will allow all content type actions to be reset. Replace the wildcard with whatever alphanumeric string is in use on their system.

---

### Post by held7over on 2013-10-10
Thanks, oldos2er, I will try that. However, I have gotten myself into a bit of trouble as I tried editing about:config and now I need to delete an entry that went very very wrong. Once I figure out how to fix that, I will try your suggestion! Thanks!

---

### Post by heir4c on 2013-10-11
Sorry for the trouble you have with my input.

---

### Post by held7over on 2013-10-11
It's no big deal heir4c. I had already been looking at about:config a couple of days ago, but hadn't found any hints as to where to look and experiment at  until your input. Worse comes to worse, I will try to just remove Firefox and it's .mozilla file and reinstall or something. I just haven't had time yet to get back to it to see if I can delete my entry into about:config or not....it's a very strange setup. I will be working on that a little later today.

---

### Post by held7over on 2013-10-11
oldos2er  --  Thanks. That deletion seems to have gotten rid of my spurious entry in about:config.

heir4c --  I managed to get an entry into about:config which looked like this:  "network.protocol-handler.expose.torrent" "boolean" set to "false" 
The situation wasn't the same as the magnet link which was giving an error that is left open why a second tab is opened, so it couldn't be done exactly like ktorrent had recommened it to be done, so either I didn't understand how to set this up this way or this direction doesn't work either. But, nice try!!! Thanks!

Anyone have any other ideas on how to fix this or what is going wrong to cause this situation?  Does it sound like something that might be fixed if I do a new install of Ubuntu 12.04?

---

### Post by held7over on 2013-10-11
I did a complete new install of Ubuntu 12.04 64bit on his Intell based 64 laptop, told it to format the "/" partitian, however, I conserved his "/home" partitian with all his personal config and data info, except I had deleted the .mozilla file before the install began. 

This didn't get rid of the problem. I am using gnome-session-fallback, but I don't see how that would have anything to do with this problem.

---

### Post by Roger Cook on 2013-10-12
In **firefox** go to edit, next go down to **preferences** and click!
Next go over to** Applications **click!
Now go down to** Torrent file** click!  or it could just be ****magnet ****if so click and go to ****use other****
When you look at this if you see **ktorrent** click it, if it is not there go to **use other**
Now go to /usr/bin/ and find and click**** ktorrent[B]
You can now change ktorrent to ask or open torrent file!

---

### Post by heir4c on 2013-10-12
Roger Cook, held7over have no "Torrent" or "magnet" in that list. The same here in my list. 


When I click on a magnet link, I have a message that DHT must be activated. (I activated that in the config of ktorrent under the "bittorrent" Tab)
( I installed ktorrent and FireFox show directly ktorrent as the default choice to download torrents)
I also add a line in about:config:
network.protocol-handler.expose.magnet  (with boolean Type and the Value: true)
After that there was "magnet" in the list (and ktorrent as default to open it.)
I try adding a line in about.config with .torrent instead of .magnet, but no "torrent" in the list.
When I click on a torrent on the torrentsite: [http://katproxy.com/](http://katproxy.com/) than I get a window with only "cancel" and "Save". But when I choose an other torrentsite I have a window where I can choose with what Program I will open it. So maybe there is something wrong on the site itself. ??
When I choose a magnet ktorrent opens automatic and I just have to click on 'OK'.

---

### Post by held7over on 2013-10-12
Thanks for your suggestion Roger Cook.  I will go over the steps you have suggested and see if I can implement any of them. Some of it I am sure I have already tried. But I have ran out of time right now, as my wife is to go into surgery tomorrow and we are getting ready, so, it may be several days before I get back and have a chance to double check things and get a reply back to you.

---

### Post by held7over on 2013-10-16
Roger -  in Applications, there is no Item labeled "Torrent File" or "Magnet" or "Magnet Link", etc., to click on. So, at that point, I can go no farther...

---

### Post by held7over on 2013-10-16
Does anyone know what file the contents of the Applications tab is held within? Maybe I could simply transfer that file from one of my computers to his computer and have this all working.........as all of my own computers have the proper entries when I click on their Applications Tabs....

---

### Post by held7over on 2013-10-21
I want to thank everyone for their suggestions and thoughts. This remains a mystery. I ran out of time and had to give the laptop back to its owner with a suggested alternative sequence of how to accomplish the same outcome. Thanks for your help!

---

### Post by oldos2er on 2013-10-21
If your issue is not solved, please remove the 'Solved' tag from this thread, otherwise people coming here looking for solutions may be sorely disappointed. Also if someone comes along later who knows the answer, they'll see the 'Solved' tag and pass your thread by, so it's to your advantage not to use 'Solved' until the problem is actually solved.

---

### Post by held7over on 2013-10-21
oldos2er -  I have done as you suggest and have UNSOLVED it.  The laptop I was working on is now located about 140 miles from me, so I will not be in much of a position to test incoming ideas to solve the problem, but maybe as you suggest someone else will. Thanks. I wasn't sure what to do in this situation...

---

