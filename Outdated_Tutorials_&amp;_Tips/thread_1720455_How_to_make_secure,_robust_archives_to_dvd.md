---
title: "How to make secure, robust archives to dvd"
date: 2011-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by oldmankit on 2011-04-03
I was looking for a way of creating archives on dvd which had two features

[LIST=1]
[*]password-protected, so that I can give them to a friend to look after and know he won't snoop.
[*]protected against read-errors.  Dvds degrade over time, and I don't want to find my carefully constructed archives are corrupted and unreadable.
[/LIST]
I posted on this [here]("http://ubuntuforums.org/showthread.php?t=1667576") and found some helpful ideas.  I thought it might help someone else who doesn't want to pay for online backup solutions but wanted their data securely backed-up in a separate geographical location.

The two key programs are dvdisaster and gnupg.  The one I used to create the .iso file was isomaster, though I am sure there are hundreds of other options for that step.  If you want to get all the tools in one go, enter the following in a terminal:
```
sudo apt-get install gnupg dvdisaster isomaster
```Here is a step-by-step account:

[LIST=1]
[*]create .tar file(s) for the data you wish to backup.  You could use a GUI like file-roller, but I used the tar command because I am familiar with it: ```
tar cvf archive.tar directory_to_archive_1 directory_2 ...
``` Please see the note at the end on file sizes if you are wondering how big to make these files.
[*](optional) compress using the terminal command ```
bzip2 -kv9 archive.tar
``` This will compress your .tar file using bzip's highest level of compression.  However, since my archives are mainly jpgs (which are already compressed) this did not reduce the size of my .tar file much, so I didn't bother with it.
[*]Time to encrypt your data.  ```
gpg -c archive.tar
``` It will ask you to enter your password twice.
[*]Using iso master (or any other suitable program) create a .iso from the .tar file(s)
[*]Now use dvdisaster to create the recovery data.  The program comes with excellent documentation on the process.  See their [home page]("http://dvdisaster.net/en/").
[*]write your iso file(s) to dvd!  Use your dvd burner of choice.  Gnome comes with brasero.  While you're waiting, now would be a good time to store the gpg password in a safe place (not on the computer with the data you are backing-up - it would be useless if the computer broke).  I saved mine in a safe place online.
[*](optional) I was intrigued to see whether the original files were actually retrievable from these layers of data protection.  Put the dvd into your drive and check to see your files are accessible now.  Test a few of them to give you confidence the process worked!  You can even use dvdisaster to verify the archive data and recovery data.  You can verify the data again at a future data to see how much (if at all) it has degraded.
[/LIST]
For me, this worked exactly as planned.  I will put the dvds in a jacket and give to a friend, knowing that if a fire or burglar comes and destroys my data, it should still be accessible with a friend.

This is my first howto, any helpful corrections or comments are welcome.

[SIZE=1]Note on file sizes:
When you calculate how many files you can put on one dvd, the first  question you need to ask yourself is whether the dvdisaster recovery  data is to be stored on the same medium as the original data, or a  separate medium.  This is fully explained in the very helpful dvdisaster  documentation (complete with diagrams explaining concepts).  I  preferred to put it on the same medium, for simplicity's sake.   Therefore the target size of my .tar file(s) is 4.4GB with 20%  redundancy (the minimum recommended) = maximum of 3.5GB per dvd.  If you were a bit over that, it wouldn't matter much, but the less redundancy data you have stored, the less chance you have of recovering all of the data perfectly if there are read errors later.
[/SIZE]

---

