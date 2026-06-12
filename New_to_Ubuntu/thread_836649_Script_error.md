---
title: "Script error"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-21
Hy all
I use Amarok, and it worked fine but for no reason now it can't fetch lyrics.I get this error message:

```
/usr/local/lib/ruby/1.8/net/http.rb:560:in `initialize': Connection timed out - connect(2) (Errno::ETIMEDOUT)
	from /usr/local/lib/ruby/1.8/net/http.rb:560:in `open'
	from /usr/local/lib/ruby/1.8/net/http.rb:560:in `connect'
	from /usr/local/lib/ruby/1.8/timeout.rb:48:in `timeout'
	from /usr/local/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/local/lib/ruby/1.8/net/http.rb:560:in `connect'
	from /usr/local/lib/ruby/1.8/net/http.rb:553:in `do_start'
	from /usr/local/lib/ruby/1.8/net/http.rb:542:in `start'
	from /usr/local/lib/ruby/1.8/net/http.rb:1032:in `request'
	from /usr/local/lib/ruby/1.8/net/http.rb:769:in `get'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:127:in `fetchLyrics'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:193
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:179:in `loop'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:179
```

Any ideas why?

---

### Post by Troll_the_Great on 2008-06-22
Nobody? :( I use gnome desktop.Could that be the problem?I heard that KDE apps work on gnome and vice versa,no?I've try remove and then reinstall it, but nothing worked.:(:(:( I've run out of ideas...

---

### Post by Dedoimedo on 2008-06-22
Hi,
Try reinstalling ruby.
Cheers,
Dedoimedo

---

### Post by Troll_the_Great on 2008-06-22
No use...:(:(:(:mad::mad::mad:

---

### Post by Troll_the_Great on 2008-06-22
Another thing.If I try to install wiki-lyrics I get this message when I try to run it:

```
Sorry...
You need one of QtRuby, RubyGTK or TkRuby to run this program
```

I didn't find anywhere those packages....

---

### Post by forestpixie on 2008-06-22
Try to install libgtk2-ruby

It didn't make any difference to mine though, I have the same error but I'm not worried about it.

There seems to be little on the amarok forum about it that's recent, you could try posting to their forum

---

### Post by Troll_the_Great on 2008-06-22
I already have that package.:(
Where can I find amarok forums?

---

### Post by forestpixie on 2008-06-22
The forum is here - [http://amarok.kde.org/forum/](http://amarok.kde.org/forum/) - good luck, if you get anywhere can you post the solution here for others.

Bear in mind I only had a quick look - so have a good searchfirst - they aren't quite so worried about rtfm from what I've seen :)

---

### Post by MasterSander on 2008-06-22
I've had the same problem, you just need to install enough things that have to do with ruby and it'll work sometime. This is probably not the best solution but the packages aren't that big.

---

### Post by Troll_the_Great on 2008-06-22
> **MasterSander said:**
> I've had the same problem, you just need to install enough things that have to do with ruby and it'll work sometime. This is probably not the best solution but the packages aren't that big.

What packages?Please be a little more specific because I really want this to work.Thanks.

---

### Post by Troll_the_Great on 2008-06-22
Looks like I won't be using lyrics... again.The interesting thing is I had the same problem, removed Amarok, didn't use it for a while and when I installed again it worked...And then broke for no reason...Odd, no?

---

