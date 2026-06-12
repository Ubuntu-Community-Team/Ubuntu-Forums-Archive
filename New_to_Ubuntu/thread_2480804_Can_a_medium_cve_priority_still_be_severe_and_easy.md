---
title: "Can a medium cve priority still be severe and easy to execute?"
date: 2022-11-10
forum: New to Ubuntu
---

### Post by donald187 on 2022-11-10
So I've been pondering Ubuntu's CVE priorities.  Especially the medium priority.  

[https://people.canonical.com/~ubuntu-security/priority.html?_ga=2.86379099.2144098909.1667930363-872091857.1661401159](https://people.canonical.com/~ubuntu-security/priority.html?_ga=2.86379099.2144098909.1667930363-872091857.1661401159)

[https://ubuntu.com/blog/securing-open-source-through-cve-prioritisation](https://ubuntu.com/blog/securing-open-source-through-cve-prioritisation)

As far as I can tell the medium priority affects fewer users than the high or critical priorities and generally requires some user intervention.  Maybe changing the default configuration or something.  Have I got this right?

I guess what I'm particularly concerned about is the possibility that a package might receive a medium priority just because it has a relatively low number of users but the consequences might be severe and be easy to execute.

Apologies if this is a little too granular.  It's just that I've thought I understood something from a distribution's documentation in the past only to find that I didn't and that I put myself at risk.

---

### Post by donald187 on 2022-11-10
Now that I think about it my question seems too simplistic.  There are apparently many factors on which the cve priority is assigned.

> 
The priority is based on many factors including severity, importance, risk, install base, software configuration, active exploitation and other factors...


[https://people.canonical.com/~ubuntu-security/priority.html?_ga=2.86379099.2144098909.1667930363-872091857.1661401159](https://people.canonical.com/~ubuntu-security/priority.html?_ga=2.86379099.2144098909.1667930363-872091857.1661401159)

Still, I may not understand something as has happened before.

---

### Post by donald187 on 2022-11-11
So this person seems to think so.

> 
[usr11elf]("https://discourse.ubuntu.com/u/usr11elf")

Hello dear Desktop team!
 The latest Thunderbird update, 91.6.1, prepared since 14.02.2022 in  the Mozilla Security PPA and already published to jammy, closes a high  risk security issue, CVE-2022-0566. Just receiving a malicious email,  without opening it, is enough to be attacked. That is the highest  possible threat. What is the reason for not pushing the button to  publish the long prepared packages into bionic, focal and impish as  well? When will this happen?
 Thank you for your work and kind regards
 usr11elf


[https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963](https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963)

and the cve is listed medium according the the Ubuntu CVE Tracker.

[https://ubuntu.com/security/CVE-2022-0566](https://ubuntu.com/security/CVE-2022-0566)

Here's the Thunderbird description of the cve.

[https://www.mozilla.org/en-US/security/advisories/mfsa2022-07/](https://www.mozilla.org/en-US/security/advisories/mfsa2022-07/)

---

### Post by donald187 on 2022-11-12
My guess is that the above example is a bit of an exception because of the need to version bump Thunderbird to correct a security flaw.
> **ian-weisser said:**
> 
The *purpose* of an LTS release is that the software doesn't change  (with important exceptions) for the life of the release. That's the  feature writ large, not a bug. "Important exceptions" do include  security patches, of course. And version-bumps for a small number of key  applications, including web browsers but generally not mail clients  (Evolution is patched, not bumped).

Thunderbird is an exception to that exception, and gets version bumps  due to sharing so much code with Firefox (which was version-bumped about  every two weeks). Since Firefox is now snapped, there are occasional  discussions about whether or not to stop version-bumping and start  patching. But for now Thunderbird still gets version-bumped. Just be  patient about it.

[https://ubuntuforums.org/showthread.php?t=2480528&p=14117889#post14117889](https://ubuntuforums.org/showthread.php?t=2480528&p=14117889#post14117889)

And the version bump seems to require extensive testing by the community.

> 
alexmurray

[@usr11elf]("https://discourse.ubuntu.com/u/usr11elf")  Indeed the delay is in the testing and approval process - and  unfortunately this takes a certain amount of time. Firefox is given  higher priority than Thunderbird because it is a lot more popular than  Thunderbird is seeded on the desktop media - and is the default web browser for Ubuntu.  With the rise of web-based mail services like gmail etc, desktop email  clients have become a lot less popular than they were 10-20 years ago. Thunderbird  has not been seeded in the desktop image since before 18.04 LTS as a  reflection of this as generally users are not using desktop email  clients - most just use the web browser to access their webmail.
 As such, testing etc of Firefox updates (and other desktop packages  seeded on the desktop image etc) are prioritised over Thunderbird so in  general Thunderbird updates will lag behind Firefox updates.  Unfortunately in a world where new security issues are found daily  across the vast array of software that is distributed in Ubuntu, there  is a constant stream of security updates which need to be prepared,  tested and released by a finite number of developers. The security and  desktop teams have to prioritise which packages to target and so we  prefer to take the approach of protecting the greatest number of users  as possible by updating the packages that are most used first. Hence why  unfortunately Thunderbird updates generally will come later - there are  just a lot more users of Firefox (and many other applications) than  Thunderbird.


[https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963/17](https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963/17)

My guess is that just patching vulnerabilities doesn't require testing by the community.  From the guidelines for preparing a patch from the Security Team Update Preparation guidelines:

> 
Make only the minimum changes necessary to fix the bug. This is crucial  both for the review process and to avoid introducing bugs or unexpected  behavioural changes. In  the rare cases when a security update must include a major version  update, it should, if possible, go to -proposed first for testing.


[https://wiki.ubuntu.com/SecurityTeam/UpdatePreparation](https://wiki.ubuntu.com/SecurityTeam/UpdatePreparation)

So a version bump seems to require testing in Proposed whereas a patch seems to not.  So I guess patches can happen a bit faster than version bumps.

---

### Post by grahammechanical on 2022-11-13
I suggest that we keep in mind that Ubuntu developers have responsibility for Ubuntu crafted software. Other developers have responsibility for their own software. It may be that Ubuntu developers become aware of a security vulnerability in Thunderbird. Ubuntu developers pass the information to the Mozilla Foundation and it becomes the responsibility of Mozilla to fix the vulnerability. Ubuntu developers have no control over the level of priority set by the Mozilla team.

It may be that Mozilla becomes aware of a security vulnerability and informs distributions such as Ubuntu. If Mozilla sets the priority to HIGH then Ubuntu developers can relax a little bit. They know the vulnerability will be fixed as soon as possible. Software such as Firefox and Thunderbird get regular updates and the fix might be pushed out during one of the regular updates. I am confident that Mozilla are not slow in sending out extra updates that contain security fixes for very severe vulnerabilities.

It might happen that Ubuntu developers can write some code to fix the vulnerability. But the code would have to be sent to Mozilla for them to merge the code and then issue an updated version of Thunderbird.

Keep in mind that security vulnerabilities are treated differently to bugs. A security fix might introduce a bug. In my opinion if the vulnerability is extremely serious then it is better to fix the vulnerability first and then to fix the bug in due time. 

 Regards

---

### Post by donald187 on 2022-11-13
Thanks.

---

### Post by ian-weisser on 2022-11-14
Random posts that a vulnerability is "severe" may turn out to be dubious. Both individual ranters and clickbait "news" sites have cried wolf before.

A truly critical CVE usually gets prioritized as "critical", not as "medium".

If you can show that the Ubuntu Security Team's review was mistaken, and that a CVE was assigned a clearly inappropriate priority, you can contact the Team and help them fix the mistake.

Generally, for most folks with questions about how security in Ubuntu works, including CVE prioritization, and who are fluent in rapidly-spoken english, I recommend listening to a couple episodes of the [Ubuntu Security Podcast]("https://ubuntusecuritypodcast.org/"). They WANT you to understand how it works.

---

### Post by donald187 on 2022-11-14
Ok thanks.  I'll give that podcast a listen.

---

### Post by donald187 on 2022-11-20
I've resolved this to my own satisfaction.  If you look at the Ubuntu CVE Tracker and look at the high cve's for Thunderbird you can see that they apply to both Firefox and Thunderbird.  Then if you look at the published dates for Firefox and Thunderbird on Launchpad for the version bumps that fixed those high cve's you can see that Firefox generally gets fixed in 1 to 3 days whereas Thunderbird generally gets fixed in 7 to 10 days.  So they're both treated as having high cve's but Firefox has so many more users than Thunderbird that it gets fixed first.  Of course this is looking at Focal and Bionic since Firefox is a deb package on them.  ian-weisser really answered my question (thanks!) but I had this annoying difficulty trying to reconcile everything.

I'll wait a few days to mark this as solved to see if someone comes on and tells me I'm wrong. :)

---

### Post by ian-weisser on 2022-11-20
Kudos for taking the time, learning the process, and following the chain to conclusion!

You have earned a celebratory cupcake. Really. Enjoy the sweet taste of really KNOWING something about how Ubuntu handles security issues.

And you are encouraged to share it. Help calm folks down who get spun up and misled and panicked by inaccurate media reports. Help stamp out rumors and guessing.

---

### Post by donald187 on 2022-11-20
Thanks!  And solved it is. :)

---

