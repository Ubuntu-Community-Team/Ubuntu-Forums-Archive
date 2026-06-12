---
title: "Timeshift driving me around the bend, again."
date: 2020-08-14
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-08-14
Hi all,

So I want to include the hidden files, in my home directory, in a snapshot. But I don't want to include ../.steam because it's full of big files I can just download again (all be it on a blazingly slow 0.8 MB/s connection)

So I set it to include /home/perrywinklesnoop/.**/ but to *exclude* /home/perrywinklesnoop/.steam/***, the problem is it just careers ahead backing up my .steam folder as soon as I start the snapshot, basically ignoring the exclusion.

There doesn't seem to be any obvious way to make it work as I want it to, I thought about changing .steam from a hidden folder to a non hidden but I think that will just cause problems (because of renaming it), a workaround would be to rename it for each snapshot and then change the name back to '.steam' but thats a bit awkward.

Any ideas?

---

### Post by GhX6GZMB on 2020-08-14
Please post a screenshot of the "Settings", "Filters" screen.

I very recently found an extremely annoying bug in the Timeshift user interface, where the last setting is not stored correctly.

That aside, I've no idea what "steam" is or why it would want to store hidden files in $HOME. Gaming?

---

### Post by CelticWarrior on 2020-08-15
> **ml9104 said:**
> That aside, I've no idea what "steam" is or why it would want to store hidden files in $HOME. Gaming?

Yes, gaming \\:D/

The default location for settings is ~/.steam and games are downloaded/installed at ~/.steam/steam. But Steam is very flexible and allows installing games pretty much anywhere else. I have a dedicated partition in a different drive and a folder in yet another drive for Steam games. The default location isn't mandatory and multiple locations can be added and even already installed games can be moved to other folders.

@jcdenton1995 Is this an option for you? Certainly not a solution for the Timeshift not respecting the exclusions but having the games somewhere else avoids the problem altogether.

---

### Post by jcdenton1995 on 2020-08-15
Here is a link to the screenshot (I'm not sure if there is a better way to post it)...

[https://imgur.com/a/rJYNWGK](https://imgur.com/a/rJYNWGK)

It looks like you may be right! I will create another exclusion and update to see if it then excludes ../.steam but includes the last exclusion in the list...

---

### Post by jcdenton1995 on 2020-08-15
> **CelticWarrior said:**
> 
@jcdenton1995 Is this an option for you? Certainly not a solution for the Timeshift not respecting the exclusions but having the games somewhere else avoids the problem altogether.

This would actually be a more suitable solution, I did at first try to exclude "~/.steam/debian-installation/steamapps/common/***" as I believed this was the folder which actually stored the game files, and I wouldn't mind backing up my steam *folder*, just not the games themselves.

Indeed it would actually be a wise move for me to backup my games to another drive as, like I said, my internet connection is excruciatingly slow. I live in the English countryside and the broadband where I am in between practically zero and 2MB/s, so I tether to my phone via USB to receive a whopping 0.5MB/s to 1.2MB/s. Every game successfully downloaded is a victory! I actually get a rush when the download speed peaks. It was literally faster in the old days to drive (or at that time get my mum to drive me) to the nearest city and buy a game from a shop :p

---

### Post by GhX6GZMB on 2020-08-15
> **jcdenton1995 said:**
> Here is a link to the screenshot (I'm not sure if there is a better way to post it)...

[https://imgur.com/a/rJYNWGK](https://imgur.com/a/rJYNWGK)

It looks like you may be right! I will create another exclusion and update to see if it then excludes ../.steam but includes the last exclusion in the list...
A better way is to scroll down when replying and clicking the "Go Advanced" button. Then you can upload pictures directly to here.


But I don't think the issue is with the "last line" bug, that applies to inclusion.

As I see it, the problem is, that you have a logic flaw. You have one line telling Timeshift to include everything under $HOME/.** and then you have a second line telling Timeshift to exclude a specific folder, although it should include everything.

How do you expect a program to resolve this?

Personally, I find CelticWarrior's solution much cleaner. Place the steam stuff somewhere else.

---

### Post by ajgreeny on 2020-08-15
For images you  wish to show in the forum please do not add large images inline with your text; use the Attachment icon, a paperclip, in the toolbar of the "Reply to Thread" window.
If you use the "Quick Reply" button that attachment icon is missing so you need to click the "Go Advanced" button.
Navigate to the image on your hard drive to attach it, click the Upload button, and it will then appear as a thumbnail in your post which, when clicked, will open full size.

Unfortunately I can't help with Timeshift; I simply backup only my home, not the OS itself, using rsync.

---

### Post by jcdenton1995 on 2020-08-15
> **ml9104 said:**
> As I see it, the problem is, that you have a logic flaw. You have one line telling Timeshift to include everything under $HOME/.** and then you have a second line telling Timeshift to exclude a specific folder, although it should include everything.

How do you expect a program to resolve this?

Yes this is true, and I had seen it.

I was actually waiting to see if anyone on here knew of a way to make one line take precedence over another, for example in the top right it says "click to edit. Drag-drop to re-order." and I had wondered if this meant that I could re-order the list so the .steam exclusion was at the top, making the program prioritise that over the ~/.** inclusion lower down in the list, thus meaning it would not override the exclusion, but alas it doesn't work that way.

I guess there is no way to selectively exclude individual files and directories that are encapsulated within a broader group that you wish to include.

---

### Post by jcdenton1995 on 2020-08-15
Thanks, that's more appropriate than using Imgur for sure :)

---

### Post by GhX6GZMB on 2020-08-15
> **jcdenton1995 said:**
> Yes this is true, and I had seen it.

I was actually waiting to see if anyone on here knew of a way to make one line take precedence over another, for example in the top right it says "click to edit. Drag-drop to re-order." and I had wondered if this meant that I could re-order the list so the .steam exclusion was at the top, making the program prioritise that over the ~/.** inclusion lower down in the list, thus meaning it would not override the exclusion, but alas it doesn't work that way.

I guess there is no way to selectively exclude individual files and directories that are encapsulated within a broader group that you wish to include.

You have to understand the purpose of Timeshift: it's a utility to restore your system to a known previous state. This means all settings and configuration files. Timeshift specifically excludes user data ($HOME) which need different handling, and OS binaries etc., which can be easily reinstalled.

Timeshift has a default "exclude list" and you have to actively add directories/files to this. If you insist on keeping the steam files as hidden in $HOME, you'll have to add every hidden directory or file to the include list except $HOME/.steam. Not a nice solution. Put the steam stuff somewhere else.

You'll see what I mean if you click the "Summary" button in the "Filters" screen.

I attach a shot of my "Filters" setup. I obviously have two users. The defined filters are what's required for recovering from a total system crash, meaning new HDD, new install etc. (been there, done that). I've included /root, although I normally exclude it during restore. But you never know.

---

### Post by jcdenton1995 on 2020-08-16
> **ml9104 said:**
> you'll have to add every hidden directory or file to the include list except $HOME/.steam. Not a nice solution. Put the steam stuff somewhere else.

Yeah I agree, I had considered manually adding every hidden file bar .steam but that would be so messy and every time a package created a new hidden file I would have to add a Timeshift inclusion for it.

No worries, I've moved my steam library.

---

