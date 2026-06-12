---
title: "Possibly OT ... PolicyKit"
date: 2011-11-10
forum: Programming Talk
---

### Post by Jethro_uk on 2011-11-10
I am trying very hard to not have a rant, but the lack of details about how "policykit" and Ubuntu work is killing me. I have managed to work out a few details, but going to the PolicyKit homepage, it seems they are on a different planet to Ubuntu (or vice-versa).

Example:

They say PolicyKit configuration is set in /etc/PolicyKit/PolicyKit.conf

guess what ? No such file on my system. Then they say that policies are stored in /usr/share/PolicyKit/policy

guess what ? No such directory on my system.

I have found /usr/share/polkit-1/actions, and amended files to get my Network Manager to allow me to make changes when logged in via X2go. But I am struggling with odd behaviour which I am convinced is down to policykit (can't use software centre, "Unlock" button is greyed out on login preferences) and I can't seem to find any decent documentation to help me.

Or am I a whinging minnie, who should shut up and be grateful ?

---

