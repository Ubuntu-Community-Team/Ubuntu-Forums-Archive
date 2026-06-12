---
title: "Ajax not working"
date: 2013-03-02
forum: Programming Talk
---

### Post by camaro1992 on 2013-03-02
HELP!

I have a new site that is in development that was programmed  elseware and moved to my server. The site was done in AJAX and we are setting an  error when we try to open it.


My programmer has been messing around  in Firebug trying to find out what the problem is here, and it's definitely the  AJAX that's causing the problem. The response from the AJAX code is the original  index page, which has the code on it to break out of the layer. I get this  message when it calls the AJAX:


"Given URL is not allowed by the  Application configuration.: One or more of the given URLs is not allowed by the  App's settings.  It must match the Website URL or Canvas URL, or the domain must  be a subdomain of one of the App's domains."


Info:

- This development site was programmed on a LINUX server and moved to a LINUX  server
- This development site is on a subdomain of my main domain
- The  main domain contains the current site that is online and being used by my  visitors.
- The inner part of the development site is layered (no tables,  frames, or iframes, just DIV, PHP, CSS, HTML JAVASCRIPT and AJAX) so when we  open the page it displays the layout but inside rather than showing the correct  page (which would come from the AJAX), it displays the MAIN site (currently  public) website inside instead.

- I cannot post a demo as I don't want  this site to be indexed yet and this forum is indexed by google and other search  engines. :-)

Thanks

---

### Post by danniel on 2013-03-03
I think that the issue is the domain name. For example, if your site is *"example.com"* you cannot make AJAX requests to *"example**.net**"*, but you can make requests to *"something.example.com"*

Are you sure you configured your application correctly? Maybe you forgot to update an URL.

---

### Post by ofnuts on 2013-03-03
> I cannot post a demo as I don't want  this site to be indexed yet and this forum is indexed by google and other search  engines

You can obfuscate the URL: [http://mysitedotcom](http://mysitedotcom)

---

