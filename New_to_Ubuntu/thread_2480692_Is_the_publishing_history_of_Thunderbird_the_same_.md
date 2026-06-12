---
title: "Is the publishing history of Thunderbird the same as that of snap Thunderbird?"
date: 2022-11-06
forum: New to Ubuntu
---

### Post by donald187 on 2022-11-06
I've been looking for a list of previously published snap Thunderbird versions for the Stable channel.  I haven't been able to find one.  But I noticed that on the publishing history of Thunderbird

[https://launchpad.net/ubuntu/+source/thunderbird](https://launchpad.net/ubuntu/+source/thunderbird)

that it skips Thunderbird 102.4.0 and 102.4.1 just as snap Thunderbird did.  That and the fact that the contact entry of snap Thunderbird is the Launchpad page for Thunderbird makes me think that the publishing history of Thunderbird is the same as that of the snaps that are published.  Do I have this right?  If not is there a list somewhere of version bumps of snap Thunderbird?

```

$ snap info thunderbird
name:      thunderbird
summary:   Mozilla Thunderbird email application
publisher: Canonical&#10003;
store-url: https://snapcraft.io/thunderbird
**contact:   https://launchpad.net/distros/ubuntu/+source/thunderbird**
license:   unset
description: |
  Thunderbird is a free and open source email, newsfeed, chat, and
  calendaring client, that&#8217;s easy to set up and customize. One of the core
  principles of Thunderbird is the use and promotion of open standards - this
  focus is a rejection of our world of closed platforms and services that
  can&#8217;t communicate with each other. We want our users to have freedom and
  choice in how they communicate.
commands:
  - thunderbird
snap-id:      k1Ml1O9GzSO2QftV0ZlWSbUfQ78nN460
tracking:     latest/stable
refresh-date: today at 06:40 PST
channels:
  latest/stable:    102.4.2-2 2022-11-03 (272) 106MB -
  latest/candidate: 102.4.2-2 2022-11-02 (272) 106MB -
  latest/beta:      107.0b3-1 2022-11-01 (270) 108MB -
  latest/edge:      &#8593;                                
installed:          102.4.2-2            (272) 106MB -

```

I wanted to see snap Thunderbird's record of version-bumps.  Whether it commonly missed some versions or not.

---

### Post by donald187 on 2023-01-14
I think this is safe to say.  Both snap Thunderbird and Thunderbird in Lunar had not published 106.1 until both did on Jan 13.  Specifically it was published in the Proposed Repository and the Candidate Channel on the same day.  The release date of 106.1 was Dec 20.  Though I suppose the exact dates may not always match up. But there seems to be a relation.

---

### Post by donald187 on 2023-05-23
And this is evidently NOT the case.  Thunderbird from the repositories is on version 102.11.0 which was published on May 15 according to Launchpad.

[https://launchpad.net/ubuntu/+source/thunderbird](https://launchpad.net/ubuntu/+source/thunderbird)

```

$ apt policy thunderbird
thunderbird:
  Installed: 1:102.11.0+build1-0ubuntu0.22.04.1
  Candidate: 1:102.11.0+build1-0ubuntu0.22.04.1
  Version table:
 *** 1:102.11.0+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

However snap Thunderbird is still on version 102.10.1 as of May 23.

```

$ snap info thunderbird
name:      thunderbird
summary:   Mozilla Thunderbird email application
publisher: Canonical&#10003;
store-url: https://snapcraft.io/thunderbird
contact:   https://launchpad.net/distros/ubuntu/+source/thunderbird
license:   MPL-2.0
description: |
  Thunderbird is a free and open source email, newsfeed, chat, and
  calendaring client, that&#8217;s easy to set up and customize. One of the core
  principles of Thunderbird is the use and promotion of open standards - this
  focus is a rejection of our world of closed platforms and services that
  can&#8217;t communicate with each other. We want our users to have freedom and
  choice in how they communicate.
snap-id: k1Ml1O9GzSO2QftV0ZlWSbUfQ78nN460
channels:
  latest/stable:    102.10.1-1 2023-05-02 (319) 106MB -
  latest/candidate: 102.11.0-1 2023-05-04 (323) 106MB -
  latest/beta:      114.0b4-1  2023-05-23 (327) 111MB -
  latest/edge:      &#8593;

```

So I think I can put this one to bed.  For the record Thunderbird 102.11.0 was released on May 10th.  So the snap version is 13 days behind at this point.

[https://www.thunderbird.net/en-US/thunderbird/102.11.0/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/102.11.0/releasenotes/)

---

### Post by idmbe on 2023-05-23
I think there is some more stages for Snap or maybe need form Maintainer push that to Snap. 
And as i see the version 102.11.0 is still on candidate.

Just check this:


**Risk-levels**

 There are four risk-levels: stable, candidate, beta and edge.   Installing from a less stable risk-level will typically mean more  frequent updates.
 The risk-levels have the following meaning:

 
[LIST]
[*] **stable**:  for the vast majority of users running on production environments.
 Releases at this risk level are as stable as they will ever get,  according to the project’s standards. Important software will only reach  this stage once it’s ready for production use and may be used in  products. There is an implied promise to avoid any changes that would  disrupt those usages. 
[*] **candidate**: for users who need to test updates prior to stable deployment, or those verifying whether a specific issue has been resolved.
 Releases in candidate are considered almost ready for going into  stable, but need some additional real world experimentation before they  move forward. Software reaching this stage will typically have passed  all available QA and review processes, since users following it expect a  high stability level. Should almost never break. 
[*] **beta**: for users wanting to test the latest features, typically outside of a production environment.
 Beta is the first level towards the stabilisation of what was before a  fast moving stream of changes. Specific projects may have slightly  different terminology for such releases (alpha, beta, etc) but all of  these are welcome on this risk level. These releases will almost  certainly have passed some sort of review and QA, but may still have  unfinished parts. Breaking changes are still relatively common here. 
[*] **edge**:  for users wanting to closely track development.
 Edge releases often include a moving stream of changes without QA or  review promises and are typically built automatically by a CI process  from an arbitrary source code snapshot. Often the CI will only publish  after some sort of automatic QA passed, and code reviews remain a good  practice, but these are project specific. Assume edge releases may break  often. 
[/LIST]

---

