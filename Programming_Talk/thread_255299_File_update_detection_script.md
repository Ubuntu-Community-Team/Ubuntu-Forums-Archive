---
title: "File update detection script"
date: 2006-09-11
forum: Programming Talk
---

### Post by madtinkerer on 2006-09-11
Hi all,

I'm hoping you can help me with a project I am working.  I host a bunch of files for different users at my workplace.  I currently have them logging into the server via ssh each into their own account.  Within each users' /home directory I have 3 directories: Activities, Plans, Assesments.  Every user has rwx rights to their own /home directory, but they have r rights in everyone else's directory as well.  What I want to do is make a fourth directory in each /home called New Arrivals or something.  I would then like to write a script that would put a link to all the files newly added to everyone's /home/* directories in each users' /home/New Additions folder, so that we can keep up to date with what we all are doing without having to check all the directories every time we login.  Is that possible?  I'd also like those links to New Additions to last for a week or so and then be wiped.  Does that at all make sense?  I figure I could set up a cron job every day to look for files that we added that day and create the links.  A problem that I forsee is that the file creation dates and the dates they are placed on the server are not necessarily the same.  I really have no idea how to script this.  Could anyone offer some advice?

Thanks

---

### Post by WagnerVaz on 2006-09-12
Why you don't try one subversion server?

---

