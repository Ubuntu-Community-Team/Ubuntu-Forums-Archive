---
title: "Configure PHP mail() to use Port 587 with Postfix?"
date: 2007-06-29
forum: Programming Talk
---

### Post by hawzor on 2007-06-29
I know what you are thinking: just set *smtp_port *= 587 in php.ini. Good advice....for a Windows system. Seems that *nix PHP configuration doesn't respect that directive at all.

I am posting everywhere I read to ask for assistance. You would be surprised how uninformative the web is about this.....You may be asking why bother with that at all? It turns out that my *DKIMproxy *implementation for Postfix only sends DKIM headers when sent through Port 587 (not when sent through 25, which my PHP webforms seem to prefer doing).

I know that the Squirrelmail project created a class called *Deliver.class.php *that somehow (~1600 lines later) sets the PHP sending port to 587. I tried to utilize this class, but it is pretty bloaty and that workaround did not seem to be panning out after several hours.

Does anybody know of any other lightweight open source class that is floating around out there for just this porpose? I promise to share the coordinates back here if found.

Alternatively, if somebody knows how to tell *DKIMproxy *to also create headers for port 25 sends, that would be much appreciated and considered elite. Early attempts to get it to work for 2 ports were met with no success.

---

### Post by cdenley on 2007-06-29
You can probably configure sendmail to use port 587.

---

### Post by hawzor on 2007-06-29
...and by that you mean what? Is all PHP handled via Sendmail wrappings?

And so how does one go about doing this?

Or are you simply saying abandon Postfix altogether?

Thanks!

---

### Post by varkey on 2008-06-08
I have exactly the same problem. Can someone please help me?

hawzor --> Did you find a solution??

---

### Post by hawzor on 2008-07-18
I never did find a solution to this problem, but I did fid a hax0r on the run from the law (not kidding he was a black hat that the FBI wanted for questioning, I later found out) who fixed it out of my sight. Then he suddenly disappeared. haha Fixed, no address to forward payment. Now how elite is that? ...changes r00t quickly... What I can tell you is that is was handled within Postfix because he never touched the PHP confs. Hope that is at least some help. 

Sorry for tardy response, I don't read Ubuntu anymore because I was harshed by some hippie moderator a year ago who didn't like the use of the term `fsckt4rd` in his posts directed at somebody who had started some scuffle with me (post sequestered). Fat lotta good this `community` has done for me. /hawzor sticks to the real deal now: Debian. KMA `Moderators!`

---

