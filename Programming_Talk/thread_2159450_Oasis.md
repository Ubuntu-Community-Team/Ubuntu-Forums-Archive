---
title: "Oasis"
date: 2013-07-03
forum: Programming Talk
---

### Post by OldManRiver on 2013-07-03
All,

Trying to get the OASIS AD automation package found at:

[http://oasis.sourceforge.net/](http://oasis.sourceforge.net/)

to work on Ubuntu.  Do not confuse this with other packages also named OASIS.  This is an OpenSource AD Automation package!

Package say only config'd and working with RHEL (RH & CentOS), so had to mod the install code, just for install and now having issues with the main code as the writer(s) of this have no clue on "best practices" when it comes to coding.

Uploading the files I've fixed to make the install run for Ubuntu.

Now working through debugging the run-time as the users defined in the oasis.cfg file nor in the oasis DB are not being recognized and so having to search to find out why!

Hope some others join me in this effort!

Cheers!

OMR

[ATTACH]244358[/ATTACH]

---

### Post by nvteighen on 2013-07-03
A couple of advices: 
1) When asking for help, please send us some example code that reproduces your problem...not the whole thing nor a link to the source code of the project you want to contribute to.
2) Given that this is code written by someone else, you should be expected to understand it to some degree and in doubt, contact the original developers... they are the people who know how this is supposed to work.
3) I see the project is a bit unmantained (if not dead), the last release being of 2007. Perhaps you should fork it by uploading the code to some code hosting service, as it makes contributing to any project a much easier task (GitHub is my favorite, but Launchpad may be a good place if you're interested in this being part of Ubuntu). If you follow this route, PLEASE, read the licensing terms, follow them and be quite explicit stating that yours is a fork of a previous project.

---

### Post by OldManRiver on 2013-07-18
> **nvteighen said:**
> A couple of advices: 
1) When asking for help, please send us some example code that reproduces your problem...not the whole thing nor a link to the source code of the project you want to contribute to.
2) Given that this is code written by someone else, you should be expected to understand it to some degree and in doubt, contact the original developers... they are the people who know how this is supposed to work.
3) I see the project is a bit unmantained (if not dead), the last release being of 2007. Perhaps you should fork it by uploading the code to some code hosting service, as it makes contributing to any project a much easier task (GitHub is my favorite, but Launchpad may be a good place if you're interested in this being part of Ubuntu). If you follow this route, PLEASE, read the licensing terms, follow them and be quite explicit stating that yours is a fork of a previous project.

nvteighen,

1. Since conversion requires re-write of the entire package, you need to download it all to understand.  I can only upload the ones that I know I've gotten or think I've gotten fixed,
2. Tried but could not find a "good contact" for the originators, so on my own, unless someone joins me here!
3. I assume the reasons the code is unmaintained are: a.) Was originally written only for RHEL releases, b.) Code is written so poorly, violating all "best practices" so that no other developers want to jump into a "pile of $%^$#", c.) When an installer fails 70-95% of potential users walk away, since they do not want to be developers, only users.

As for a "new fork" yes it needs it, but besides the GitHub and LaunchPad you mentioned, could go on Google Source or SourceForge, so not sure what best target launch would be and since the code is so buggy, really need 3-5 other developers to join in, where we will have to divide up code to conquer it.  I would not feel comfortable releasing anything, until the program works, at least in rudimentary form, then and only then would I publish anything about it.

I just do not like my name associated with non-working, poorly planned and executed, and crippled packages.  A caviat release statement can come with the package, when working at rudimentary level, stating what is working well and what still needs work.

Also I would not feel comfortable without developers joining with RHEL (CentOS or Red Hat), Debian, Ubuntu and at least 2 more Linux flavors doing tests on their platforms, before I would call it solid enough for a release.

Hope you understand!

Cheers!

OMR

---

### Post by zQ6ML3J on 2013-08-02
All,

Finally got a resolution to my problem on PHPMailer at: [http://ubuntuforums.org/showthread.php?t=2115666](http://ubuntuforums.org/showthread.php?t=2115666), which was pertainent to PHPMailer and PHPList, so now that emails are actually working there, can pursue this package and it's fixes further!

Had to open thread at: [http://ubuntuforums.org/showthread.php?t=216496](http://ubuntuforums.org/showthread.php?t=216496) because of the screwup on my userID, due to system crash here!

Cheers!

OMR

---

