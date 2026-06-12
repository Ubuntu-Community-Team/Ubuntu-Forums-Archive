---
title: "firefox address bar search"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by cmcanulty on 2013-02-06
I am travelling using various wifi's and my firefox awesome bar has been hacked to search with roadrunner instead of google, though it says google in about:config see screenshot please help

---

### Post by kanikilu on 2013-02-06
Who is your internet service provider? If RoadRunner, than I don't think this is so much a "hack" or even malware, as it is your ISP forcing this search "service" on you.

A Google search (ironic, I know) for "[dnssearch.rr.com redirect]("https://www.google.com/search?q=dnssearch.rr.com+redirect")" brings up a lot of people with the same question.

Someone on the Mozilla support forum supposedly has a workaround:

[http://support.mozilla.org/en-US/questions/763866](http://support.mozilla.org/en-US/questions/763866)

Out of curiosity, when you type "www.google.com" in the browser bar, do you get redirected, or does it take you to Google?

If you're not on RoadRunner, I don't really know what could cause this but malware, and I've never seen any on Linux. Maybe your DNS servers got changed?

This Macworld thread suggests changing your DNS settings:

[http://hintsforums.macworld.com/showthread.php?t=113660](http://hintsforums.macworld.com/showthread.php?t=113660)

Perhaps you could also check your /etc/hosts file to see that no wonky redirects are going on there :confused:

---

### Post by cmcanulty on 2013-02-07
My home service is charter and as I said I am not home but traveling and this happened.And it is not happening with address searches like [www.gooogle.com](www.gooogle.com) but with address bar searches such as "dog". Here is my etc/hosts file
```

127.0.0.1	localhost
127.0.1.1	Acer

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
all the fixes on that link are for addresses not keyword.url which is set correctly to google for my laptop

---

### Post by Cheesemill on 2013-02-07
I've never used the address bar to perform searches as it always redirects to my ISP.

The address bar isn't meant to search for anything, it just tries to perform a DNS lookup on whatever you type into it. It's up to the DNS server you are using what to to with an address that doesn't resolve correctly. In your case (and mine) as you are using the DNS servers of the ISP you are currently connected to they just redirect the address you typed to their own search engine.

Your browser hasn't been hijacked at all, if you want to search using Google then you should use the search box rather than the address bar.

Edit - Just did some research on the awesome bar and it's not meant to perform online searches, it's extra functionality apart from being the address bar is that it searches through your history and bookmarks as you type

---

### Post by mcduck on 2013-02-07
> **Cheesemill said:**
> I've never used the address bar to perform searches as it always redirects to my ISP.

The address bar isn't meant to search for anything, it just tries to perform a DNS lookup on whatever you type into it. It's up to the DNS server you are using what to to with an address that doesn't resolve correctly. In your case (and mine) as you are using the DNS servers of the ISP you are currently connected to they just redirect the address you typed to their own search engine.

Your browser hasn't been hijacked at all, if you want to search using Google then you should use the search box rather than the address bar.

Edit - Just did some research on the awesome bar and it's not meant to perform online searches, it's extra functionality apart from being the address bar is that it searches through your history and bookmarks as you type
Actually the address bar on Firefox *is* supposed to do a google search and pick the first result if whatever you typed there isn't a valid URL.

The desired search service can be forced through about:config, the relevant key is "Keyword.URL".

---

### Post by Cheesemill on 2013-02-07
Interesting.

I would expect that Firefox falls back to its default search only if a valid URL isn't entered. As the ISP in question is providing a redirection to its own search engine as a valid result for the search term then the Firefox search probably doesn't get called in the first place.

I've never known about this behaviour as I've always used ISP's that redirect in this fashion.

---

### Post by cmcanulty on 2013-02-08
as I said my keyword.url is set to google it just isn't going to google

---

### Post by Cheesemill on 2013-02-08
I'll try and explain a bit better.

The address bar will only conduct a Google search if the text entered doesn't resolve to a valid address, for example if you type ubuntuforums.org in the address bar you want to go straight to the site rather then performing a search for ubuntuforums.org.

Typing 'dog' into the address bar *usually* wouldn't resolve to an actual site, so instead Firefox sends you to a Google search for 'dog'.

However, because you are using DNS servers that belong to the ISP you are connected to, they can return whatever value they want for a DNS lookup. Instead of their DNS servers saying 'dog' isn't a valid address as you would expect, they will say 'dog' is a valid address, and its IP address is x.x.x.x (insert ISP's favourite search engine here). This is why you are redirected to their search engine.

By returning a valid address for your search Firefox is prevented from falling back to performing a Google search.

As I mentioned earlier I never even knew about this functionality of the Firefox address bar until this thread, all of the ISP's I've had perform this type of DNS redirection.

At the end of the day that's why you have a seperate search bar, you should use this for your searches and only use the address bar for properly formed addresses.

If you do want to keep using the address bar for searches then you will have to change your network settings so that they point to a properly behaved DNS server.

---

### Post by SeijiSensei on 2013-02-08
The real problem is the ISP.  Some ISPs routinely hijack DNS queries to port 53 and redirect them to their own servers where they sell ads.  Changing the identity of your search provider in Firefox cannot remedy this because the ISP is behaving badly. 

One complicated workaround would be to set up an OpenVPN tunnel to some other machine you control and push all your DNS queries through the tunnel where they cannot be intercepted.

---

### Post by williamzach221 on 2013-02-08
[LEFT][COLOR=#484848][FONT=Open Sans]The Reset Firefox feature can fix many issues by restoring Firefox to its factory default state while saving your essential information.[/FONT][/COLOR]
[COLOR=#484848][FONT=Open Sans]To Reset Firefox do the following:[/FONT][/COLOR][/LEFT]

[LIST]
[*]Go to Firefox > Help > Troubleshooting Information.
[*]Click the "Reset Firefox" button.
[*]Firefox will close and reset. After Firefox is done, it will show a window with the information that is imported. Click Finish.
[*]Firefox will open with all factory defaults applied.
[/LIST]
This may helps you.
thank you

---

### Post by cmcanulty on 2013-02-09
OK thanks for the very informative responses

---

### Post by mcduck on 2013-02-10
For some reason, I've actually solved this problem before by editing the about:config key. (had the trouble copule of times when travelling in UK, copule of operators redirected the search to their own site instead of Google). Haven't ahd the problem since manually setting the search engine I prefer: [http://kb.mozillazine.org/Location_Bar_Search]("http://kb.mozillazine.org/Location_Bar_Search")

Anyway, if you've tried that and it didn't help, a simple workaround would be setting up a basic keyword search: [http://kb.mozillazine.org/Using_keyword_searches]("http://kb.mozillazine.org/Using_keyword_searches")

---

### Post by PhilGil on 2013-02-10
If you typically use the address bar to search you may want to give the [Omnibar Add-On]("https://addons.mozilla.org/en-US/firefox/addon/omnibar/") a try. It integrates the Firefox search and address bars (like Google Chrome), but is more configurable than the Chrome omnibar.

I've been using it for a couple of years and it works well.

---

### Post by cmcanulty on 2013-02-10
thanks I am trying both

---

