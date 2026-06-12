---
title: "Announcing New: &quot;UbuntuForums 'system-info' Sticky's."
date: 2022-06-21
forum: New to Ubuntu
---

### Post by MAFoElffen on 2022-06-21
* This is (On-Purpose) a duplicate post to one in the "Hardware" Section, as approved by the Admin Staff.)

I am proud to announce a new tool for Ubuntu to help Members on the  Ubuntu Forum to be able to help Users in need. "The tool" is a script  that reports a system's hardware and system settings information, in  ways that are important to the diagnostics and health of a system. It is  easier to help people in need when you know what their system is, and  what we are recommending solutions for. As well as 'things' that are  reported abnormally, in what should be a healthy system.

(The  Forums Staff has announced this recently in the Staff area. I announced  it's general release in the Ubuntu Members (Only) area back in  2022.02.08. I was asked by the Admin Staff to post announcements in the  general member's areas.)

The information for this script- What it  does, where to get it on the Forum's GitHub Repo, and how to run it...  Are contained in two Sticky's on the Forum, in the "New To Ubuntu" and  "Hardware" Sections.

The script is actively maintained by myself  and the contributors, as well as been reviewed by the Forum's staff. It  has been in use helping our Members for almost a year now, with great  success. There are no malicious commands, nor anything contained in it  that can harm a system.

This script was meant mainly for Ubuntu  and it's derivatives... It does report specifics that are "Ubuntu."  Though, care was taken while I wrote it to make it work for Linux as a  whole. (Without those 'Ubuntu' specifics.) It has already helped many  Users of Linux of other Distributions and Branches (besides just Ubuntu  users).

There is one caution when recommending 'posting' the  results of this script to General User's... The generated report is  sanitized to mask sensitive data. While running the script, there is an  "Eye's Only" mode displayed with 'less' that will give the user running  the report a detailed view of unmasked results. Those detailed, unmasked  results should not be posted publicly. 

Of course, a user should  not have to post the results on the Forum... I wrote four alternative  ways to upload the report to various Pastebins for review. Posting the  results to the Forum in a post should be thought of as an alternative  backup method to that. All they should have to do is to post the link to that PasteBin.

It is easier to recommend a sound solution  when you can see what is there and going on. We hope that this script  makes life easier for all who need it. I hope that it promotes  diagnosing issues and recommending solutions for those issues easier and  more concise.

---

### Post by TheFu on 2022-06-22
Do the locations of the pastebin posting still mandate logins for view-only access?

---

### Post by coley9225 on 2022-06-22
MAFoElffen, Thanks for the script. I first saw it referenced in a thread in April. I ran the script(didn't upload the output) just to view the info there. It contains a tremendous amount of info that I don't understand, but for me it's a 'list' of things to learn more about.
I followed the links provided to the script and copied into a file, so I can compare the output to a command, thereby giving me a chance to learn more about the commands and even more about what makes my system tick. All of you folks that worked on this have done a great job. Keep up the good work.

---

### Post by #&amp;thj^% on 2022-06-22
> **TheFu said:**
> Do the locations of the pastebin posting still mandate logins for view-only access?

Great Question, here is all I know: [https://www.echosec.net/blog/what-is-pastebin-and-why-do-hackers-love-it](https://www.echosec.net/blog/what-is-pastebin-and-why-do-hackers-love-it)
When I view one from a Poster it checks first if I'm logged in, but I have seen other pastes while not logged in.
Would Like a Clear answer for this myself....
> There is one caution when recommending 'posting' the results of this script to General User's... The generated report is sanitized to mask sensitive data. While running the script, there is an "Eye's Only" mode displayed with 'less' that will give the user running the report a detailed view of unmasked results. Those detailed, unmasked results should not be posted publicly.


---

### Post by TheFu on 2022-06-22
> **coley9225 said:**
> MAFoElffen, Thanks for the script. I first saw it referenced in a thread in April. I ran the script(didn't upload the output) just to view the info there. It contains a tremendous amount of info that I don't understand, but for me it's a 'list' of things to learn more about.
I followed the links provided to the script and copied into a file, so I can compare the output to a command, thereby giving me a chance to learn more about the commands and even more about what makes my system tick. All of you folks that worked on this have done a great job. Keep up the good work.

It is a good script.

MAFoElffen's script which probably had inputs from 20+ others over the last 8 months, is specifically for troubleshooting almost anything on an Ubuntu server or desktop.  Some of the commands have extra processing and options that most users wouldn't use.  Each is designed to provide extremely dense information, so beware.

Most of the long-timers have either scripts or shell aliases to capture specific information based on our experience and needs.  This usually means having more information than the average person would, but not every possible detail. Plus, they are customized for how we each, individually, do things.  I barely use UUIDs to mount storage, so those aren't very important to me. But for almost everyone else in the world, UUIDs are all they know for storage mounts.

The right tool (and options) for the right need is the goal.

---

### Post by MAFoElffen on 2022-06-23
Yes. the PasteBin at paste.ubuntu.com, when viewing it wants you to log in to view. Funny thing is, that it doesn't require a login to upload a paste to it. (LOL) The User is given the choice to upload to a pastebin, or not. If not, the location of the report and it's filename is given, so that the User came attach it to a post.

If the utility 'pastebinit' is not installed, I have three other fallback methods in the script to use other common Linux utilities (curl, wget and nc) to upload to a pastebin. 'cur' and 'pastebinit' go to paste.ubuntu.com. 'nc' and 'wget' go to termbin.com...

Someone mentioned "February"... STABLE has had 52 commits in the last 10 months, so what that User used has changed a lot since February.

I just pushed New Version 2.00-00 tonight to DEV/TEST for testing.

 It now determines what it is running on whether an Ubuntu Flavor, something derived from Debian in the Debian Branch, or outside of the Debian Branch, and runs the report without errors. 

It now asks if you want to create an archive file, if the size is above 19.5kb, so that the User can attach to a post on the forum. Otherwise the User can attach to a post as a Text file (if below 19.5kb).

It checks for missing command and utilities used in that script, will list those out, and give the User the chance to Exit (to install those) or to continue... The messages say that it will continue as best as it can... But with the new version, there has been a lot of error handling and alternate methods to continue without error, just showing less detailed information from those missing utilities. It is to the point, even though I wrote it for Ubuntu Flavors, it will now run on Debian Branch, RHEL, SUSE, Arch, etc, and run without errors, just showing different levels of information.

Yes, it has a lot of information in the report. If you can learn to interpret the information in it, and know what is abnormal, from what should be normal... That is the key. A lot of old timers here can look at it and say "Here's your Problem..." For newer Users, there is some understanding of Linux systems needed.

I tried to do some of that interpretation in the code, by giving a translation in some places. But there is still some interpretation needed in other sections.

TheFu himself had asked me, what does this message mean, meaning how did  I determine this? ("The system is connected to the Internet with DNS") I  talked him through the logic tree for that... There is a network device  up, can ping to a know ip address, and also ping with a DNS name of  that same know location... A basic trouble shooting decision tree for  that. The rest of the script has those same kinds of logical  troubleshooting decision points.

I could really use some help with creating a Wiki on how to interpret the data contained in the Report. I'm busy with coding and maintaining this script. I spent my whole day off today making changes for this new release. I commented the code so other people can follow it... But some skills in Linux itself are needed to know what the data displayed means.

That is why I've written over 1600 lines of code in this script to make it work, to make it flexible, and adaptable. I wanted it to be useful and helpful to Users here, to be able to use as a tool, so they didn't have to post 20 times to ask a User asking for help, what hardware was there or how something was configured.  A lot of the extra command options and filters I wrote, weeds out what the test group felt was not important for diagnostics. 

A lot of the rewrites I did was to replace having to use some Linux Utilities that were not installed by default in current Ubuntu, so a User did not have install something special. There are some that were not default installed, would help with specific answers... But can still run without them. If you learn what is in the reports, you can see where, if a User would need to install those to help with their specific issue, you can recommend that they install those and rerun the report to see the related information they would provide.

The script itself is fairly User Friendly. It tries to explain what is going on, and what to do. It gives the User some choices. It is interactive and tries to keep the User's attention and keep them informed... Instead of just running, leaving the User wondering what is going on. It does not (only) generate a report, that has to be viewed later by other means.

---

