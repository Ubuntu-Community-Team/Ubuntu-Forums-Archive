---
title: "Bash script to read my tv show file names and move to folder"
date: 2016-12-01
forum: Programming Talk
---

### Post by rbishop on 2016-12-01
Hello All,

I hope you guys can help me as I have been racking my brain for the last few days on this one and have yet to come up with a workable solution.  Any help you can give me is very much accepted.  I am trying to automate my FTPing of files to my file server as much as possible so I don't have to manually change directories for every one or two episodes/Series I get.  As the Title says, I am looking for a script that I can have set to run that will look at a folder and read the files in that folder and then move those files to their respective TV show and Season folders.

Files will be uploaded to the following directory:

/UPLOAD

Files will have names like :

TV.Show.Name1.S01E10.avi
TV.Show.Name2.S02E03.avi
TV.Show.Name2.S03E09.avi
TV.Show.Name3.S01E01.avi

The folders these shows are stored in are setup like this:

/AV-Files/TV--> /TV Show Name1--> /Season1--> files
/AV-Files/TV--> /TV Show Name2--> /Season2--> files
/AV-Files/TV--> /TV Show Name3--> /Season3--> files

Thank you in advance.  Any ideas or suggestions you guys can give me would be greatly appreciated.

---

### Post by TheFu on 2016-12-01
I won't create the script for you, but I will happily provide feedback and best practices and how-to links.  Teaching you to fish, as it were.  This way, when something trivial changes, you won't be stuck and will easily tweak the script to handle the next situation.  BTW, please use directories names in the expected format .... not including '-->' - if those characters are in your names, the script will be much harder than if you sanitize the names.

BTW, I've been running media centers for years - XBMC, Plex, Kodi, 7MC and understand the directory layouts those systems require.  I'm at the point where multiple disks are needed to hold everything.  Thankfully, the media server I use understands that idea and I don't have to merge disks into a single file system.  

First of all, don't use FTP.  Use sftp. If your provider doesn't support that, fire them today.  There just isn't any excuse for them requiring you so transmit your login credentials in the clear, unencrypted.

Now, let's begin by writing out the specific steps, as code comments, to make what you want to happen, happen.  Those steps don't need to match 1-for-1 to 1 line of code. High level is good to begin.  

Next, what commands would you type into a terminal to accomplish those steps?  That will be the start of a script.

I do some things that others don't do for my own sanity.
* Swap most '.' for '_' - except where necessary.
* Use '-' instead of . or _ between different parts of the filename.  resolution, episide data, etc.
  For example, Agents_of_SHIELD-407-Deals_With_Our_Devils-720p.mkv is my name for the episode recorded last a few days ago. It is located in /DD/T3/Agents_of_SHIELD/S4/ directory.  I have T1 and T2 directories which are located on other disks.  A complete show is always on a single disk for my sanity.  I don't want anything to be longer than it needs to be.  /D/ and /Dd/ are already full.

So first, I find all '.' and replace those with '_' using the perl rename tool.  
```
$ rename 's#[.]#_#g; *avi *mkv *mp4; # This renames too much - extensions too!
$ rename 's/_avi$/.avi/g' *avi # to fix that part; need to fix the other 2 file types
$ rename 's/_mp4$/.mp4/g' *mp4
$ rename 's/_mkv$/.mkv/g' *mkv
# Next I would need to recognize the different parts {episide}-{ep-title}-{resolution} and put '-' in for '_'
# then determine the root of the filename "Agents_of_SHIELD", for example, then building the correct
# directory wouldn't be too hard
```

Ain't pretty, but it should work.  I didn't test the first regex (pattern match). It may need some tweaking, since '.' means to match any character, so putting it into [.] should match only a '.' (dot).  Clear as mud?  Test on a set of test filenames, please. Don't risk real files.  Just create a temporary directory under /tmp/ and create some empty files using **touch {name}**. I'd put the creation and cleanup commands into a script too. ;)  Try to make hard filename problems to test with.  For example, punchuation, spaces, single and double quotes can cause issues in bash scripts.  If you decide not to just remove those from the names completely, you'll need a way to handle them.  I remove weird characters to keep my scripts easy.

Also, you'll probably want some error handling, so if the target disk is full, the script exits with that error.  Full disks are an issue for every OS, so it is probably best to stop with 2-4G left.

Beginning Bash scripting: [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)
Advanced Bash scripting: [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

Does that get you started?

I must admit that when a bash/sh script gets over 1 page in total length, I usually switch to perl.  Perl is a full programming language and doesn't need workarounds to do normal programming stuff, plus I've been programming in perl for over 20 yrs now.  Ruby or python would be fine too, if you know any of those.

Just looked at my push-movies script - it is much easier than the script for TV shows. No episides, no ep-titles to deal with. Would it make sense to start with that first?

Anyways, hope this helps.

---

### Post by rbishop on 2016-12-02
Thanks for the response "Fu".  It helps to see/hear what other people have done or do in similar situations.  I only use FTP on my local network, never over public internet.  

So in your opinion would this job/task be better suited for Perl to handle?  

Thanks again for your response.

---

### Post by TheFu on 2016-12-02
The language used is really personal preference.  Perl is **my** preference, but if you don't already know it, most people would choose something else. What programming languages do you already know?  If none, then start with python.

If you don't want to learn **any** language, even bash, then you are stuck. Perhaps moving things manually will suffice?  With tab completion, this isn't very painful.

Plain FTP isn't exactly convenient. ssh/scp/sftp are and still secure thanks to ssh-keys.  Plain FTP should have died with Telnet around 1995. Wish Redhat would stop teaching it as the way to setup jumpstart boxes.

---

### Post by Herbon on 2016-12-15
Very helpful post!!!

---

