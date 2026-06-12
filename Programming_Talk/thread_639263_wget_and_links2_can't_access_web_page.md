---
title: "wget and links2 can't access web page"
date: 2007-12-13
forum: Programming Talk
---

### Post by go_beep_yourself on 2007-12-13
Why do none of these work?

wget [http://www.blackcats-games.net/signup.php](http://www.blackcats-games.net/signup.php)

links2 -source [http://www.blackcats-games.net/signup.php](http://www.blackcats-games.net/signup.php)

links2 -dump [http://www.blackcats-games.net/signup.php](http://www.blackcats-games.net/signup.php)

The only way I've been able to access that page is by clicking a link. I need to be able to access it from a script, so I can know when registration opens. Is there any possible way to do this? Here's what I have.

wget -P/tmp [http://www.blackcats-games.net/signup.php](http://www.blackcats-games.net/signup.php) > /tmp/logfile 2>&1; if (grep -q 'current user account limit' /tmp/signup.php); then DISPLAY=:0 xmessage 'account registration opened at blackcat'; cat /tmp/logfile; fi; rm -f /tmp/signup.php /tmp/logfile > /dev/null 2>&1

---

### Post by Majorix on 2007-12-13
Actually you can't access their page by handwritten url. You have to click on the "register" link on the front page, and sadly that's the only way there is to it. I think they have a server side script that blocks bots from signing up automatically. Understandable, but there are better ways to it than blocking the whole access to the page by hand.

---

### Post by slavik on 2007-12-13
it checks the referrer, if the refferer is not itself, then don't allow registration. simple php stuff :)

---

### Post by go_beep_yourself on 2007-12-13
> **Majorix said:**
> Actually you can't access their page by handwritten url. You have to click on the "register" link on the front page...

I said that already. Don't state the problem. I already did that. State the solution.

---

### Post by go_beep_yourself on 2007-12-13
> **slavik said:**
> it checks the referrer, if the refferer is not itself, then don't allow registration. simple php stuff :)

Okay, how can the referrer be spoofed?

---

### Post by Majorix on 2007-12-13
> **go_beep_yourself said:**
> I said that already. Don't state the problem. I already did that. State the solution.

There is most likely no solution.

---

### Post by go_beep_yourself on 2007-12-13
> **Majorix said:**
> There is most likely no solution.

How does the server know that a link was clicked on instead of going directly to the page?

---

### Post by slavik on 2007-12-13
via the refferer ... unfortunately, I don't know enough about web related stuff to know how to spoof such things :(

---

### Post by go_beep_yourself on 2007-12-13
> **slavik said:**
> via the refferer ... unfortunately, I don't know enough about web related stuff to know how to spoof such things :(

Spoofing? This sounds like a question for the remote exploit forums.

---

### Post by go_beep_yourself on 2007-12-13
> **slavik said:**
> via the refferer

What referrer are you speaking of? I'd like to know specifically, so I can look up some information on this.

---

### Post by go_beep_yourself on 2007-12-13
Nevermind, found it here.

[http://en.wikipedia.org/wiki/Referer](http://en.wikipedia.org/wiki/Referer)

---

### Post by go_beep_yourself on 2007-12-13
> **Majorix said:**
> There is most likely no solution.

You speak of lies.

"Referer logging is used to allow websites and web servers to identify where people are visiting them from, for promotional or security purposes. Since the referer can easily be spoofed (faked), however, it is of limited use in this regard except on a casual basis."

That's from the wikipedia page that I posted earlier.

---

### Post by cwaldbieser on 2007-12-13
wget has a --referrer option.  The referrer is just an HTTP header.

---

### Post by go_beep_yourself on 2007-12-13
How can I know what the http referrer is being sent to the server that I should use with wget?

---

