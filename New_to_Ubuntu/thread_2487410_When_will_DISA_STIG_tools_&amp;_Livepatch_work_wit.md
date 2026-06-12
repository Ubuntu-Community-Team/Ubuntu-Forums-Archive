---
title: "When will DISA_STIG tools &amp; Livepatch work with the latest Ubuntu release/kernels?"
date: 2023-06-03
forum: New to Ubuntu
---

### Post by aocorporation on 2023-06-03
[]("https://askubuntu.com/posts/1470533/timeline")  
          
                                        Specifically, 22.04.2 and kernel 5.19.0-43-generic
 Seems, I'm going to have to downgrade to 20.04, I just want a  hardened system backed by government (military) standards for security  research. Am I wrong for doing so? Additionally, how would I prevent a  full system upgrade when going about the update center to prevent my  system from upgrading out of Livepatch support (ergo going from 20.04 to  22.4.2 accidentally in an automatic update)?  What security flaws may I  embark on by downgrading?
 There's not a whole lot of documentation on this.

---

### Post by TheFu on 2023-06-03
The latest Ubuntu is 23.04 and to my knowledge, nobody attempts to create STIGs using non-LTS releases.

Nobody here works for Canonical. Everyone is a volunteer.

If you'd like an official answer, call the number on your Canonical Support Contract to let them know that your organization cares about these things.  I think it usually takes 2+ yrs for an LTS STIG to be figured out, but I don't watch that stuff too closely.

---

### Post by MAFoElffen on 2023-06-03
I also have no connection with Canonical, and the people to talk to about that would be Canonical's Ubuntu Pro Team. Which, like me, then you will referred to the DISA Helpdesk at: [EMAIL="disa.stig_spt@mail.mil"]disa.stig_spt@mail.mil[/EMAIL]

RE: [https://discourse.ubuntu.com/t/ubuntu-pro-beta-invitation/30957/8](https://discourse.ubuntu.com/t/ubuntu-pro-beta-invitation/30957/8)
There, when asked about when the toolkit was scheduled to roll out:
> 
henrycogill-- March 13, 2023

Hi, this is still in development and we are intending to release it by May 2023.
Hope that helps.

When, I, as a customer asked the Ubuntu Pro Support Team about this... The toolkit is in beta, marked as such, until DISA publishes the STIG's for Ubuntu 22.04. It's a chicken before the egg kind of thing.

As my understanding, and I am just a user... So I am no one as this goes. So what I am told, is that DISA STIG's are published by DISA. If you look at DISA's Library:  [https://public.cyber.mil/stigs/downloads/?_dl_facet_stigs=operating-systems%2Cunix-linux](https://public.cyber.mil/stigs/downloads/?_dl_facet_stigs=operating-systems%2Cunix-linux)

...There is no STIG published yet by DISA for ubunt past 20.04 LTS...
> 
**DISA-STIG for Ubuntu**

     Together with Canonical, DISA has developed STIGs for Ubuntu. The U.S. DoD provides the [STIG checklist]("https://public.cyber.mil/stigs/downloads/?_dl_facet_stigs=operating-systems%2Cunix-linux"), which can be viewed using [STIG viewer]("https://public.cyber.mil/stigs/stig-viewing-tools/"), and [SCAP content for auditing]("https://public.cyber.mil/stigs/scap/"). The versions of Ubuntu that have STIGs available by DISA are marked on the table below.


But, looking at this from: 
> 

**STIGs**


 **Critical Updates**

 To provide increased flexibility for the future, DISA has updated the  systems that produce STIGs and SRGs. This has resulted in a  modification to Group and Rule IDs (Vul and Subvul IDs).
 Test STIGs and test benchmarks were published from March through  October 2020 to invite feedback. New and updated STIGs are now being  published with the modified content.
 New releases of STIGs published prior to this change will include the “legacy” Group and Rule IDs as XCCDF ident elements.
 For all questions related to STIG content, please contact the DISA STIG Customer Support Desk at [EMAIL="disa.stig_spt@mail.mil"]disa.stig_spt@mail.mil[/EMAIL].

 




Leads around in a circle, with DISA, not yet publishing what those modified requirements are for things later than 2020... Right? That is how I read that.

There is OpenSCAP, which has reviewed what that means for Ubuntu 22.04 ([https://static.open-scap.org/ssg-guides/ssg-ubuntu2204-guide-index.html](https://static.open-scap.org/ssg-guides/ssg-ubuntu2204-guide-index.html)), but how I read from DISA, that is still a best-guess, until DISA publishes the revisions to the STIG's.

So yes, I would contact [EMAIL="disa.stig_spt@mail.mi"]disa.stig_spt@mail.mi[/EMAIL] and get an official answer from them on when that timeline is now expected from them. May 2023 has now passed by.

---

### Post by grahammechanical on 2023-06-03
update/upgrade> how would I prevent a  full system upgrade when going about the update  center to prevent my  system from upgrading out of Livepatch support  (ergo going from 20.04 to  22.4.2 accidentally in an automatic update)?

I am using 20.04.06 with livepatch and ESM activated. Running update/upgrade does not automatically upgrade one LTS to the next without user approval. After running Software Updater I get an advisory that 22.04 is available and an option to upgrade. I refuse because with Extended Security Maintenance (ESM) 20.04 gets an extra five years support beyond the normal end of support date.

When that date arrives I shall decided to do a fresh install to 24.04.  Or, if I feel lucky I might try doing online upgrades to 22.04 and then  to 24.04.

You could always open Software & Updates?updates tab and set Notify me of a new Ubuntu version to "Never." That will prevent starting the upgrade to the next LTS by mistake.

 As for the other matter, there is this official information:

[https://ubuntu.com/security/certifications#stig](https://ubuntu.com/security/certifications#stig)

Regards

---

### Post by TheFu on 2023-06-03
**apt** or **apt-get** won't magically, unintentionally, move from a major release to another.  

**apt upgrade** and **apt full-upgrade** don't do that.  They just update software for the current release.  full-upgrade can take you from 22.04._1_ --> 22.04._2_, but that's about it, at least not without lots of manually file edits that you wouldn't do accidentally.

---

### Post by homurawasframed on 2023-09-07
I emailed the [email]disa.stig_spt@mail.mil[/email] address this morning asking if they had an updated availability date for a 22.04 LTS STIG. This is their response: 

> Unfortunately we can&#8217;t as there are steps in the release process that  are outside of our control. I can say that a 22.04 STIG is being worked  on and hopefully should be out this year.

---

