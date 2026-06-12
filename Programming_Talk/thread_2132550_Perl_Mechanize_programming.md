---
title: "Perl Mechanize programming"
date: 2013-04-05
forum: Programming Talk
---

### Post by kdavies on 2013-04-05
Hi

I access a password protected website and have to repeat a task several times.

I am hoping this can this be automated with the use of the Mechanize perl script.

Is there a way to record the selections I make on the site that can then be used as a template for a perl script?

I am new to perl programming and use Ubuntu for my desktop.

Cheers

Kevin

---

### Post by schragge on 2013-04-05
Take a look at [WWW::Mechanize::Shell(3pm)](http://manpages.ubuntu.com/manpages/precise/en/man3/WWW::Mechanize::Shell.3pm.html)

---

### Post by kdavies on 2013-04-05
ok

---

### Post by Habitual on 2013-04-05
[Hack 21 WWW::Mechanize 101]("http://spideringhacks.org.ua/0596005776_spiderhks-chp-2-sect-17.html")

---

### Post by kdavies on 2013-04-06
THanks for the info.

The site does not want to let me in unless I am doing something wrong.

In Mechanize shell:
get [http://websiteIwanttovisit.com](http://websiteIwanttovisit.com)
Retrieving [http://websiteIwanttovisit.com(200)](http://websiteIwanttovisit.com(200))
fillout         # interactive form for login and password
submit
200
browse    # Open results in a web browser takes me back to the login page

In the message console it reports a Javascript check login

---

### Post by schragge on 2013-04-06
TBH, I never used WWW::Mechanize as all my automated login needs are covered with something as simple as:
```

#!/usr/bin/perl -w

use Net::Netrc;
use URI;
use LWP::Simple;

($login, $password, undef) = Net::Netrc->lookup('example.com')->lpa;

$uri = URI->new('https://www.example.com/cgi-bin/login.cgi');
$uri->query_form(name => $login, passwd => $password, submit => 1);

$contents=get($uri);

```

---

### Post by kdavies on 2013-04-06
Ok

This is all unfamiliar to me.

If thats the login done, I then want to loop x times for the following two pages.
The next page has radio buttons to select, a text box to put a value into and a submit button to click.
The following pagen then has a confirm button to submit.

---

### Post by kdavies on 2013-04-07
Hi 

Thanks for your input and programming tips.

I found and worked out a solution using HTTP::Recorder.

With Recorder you set your local pc as a proxy, navigate to your website of interest, do the tasks you want to repeat in a script, the results are saved. Then to make them a perl script add the Perl and Mechanize headers.

Job done.

Found it in a web testing article.
[http://www.perl.com/pub/2004/06/04/recorder.html?page=1#control_panel](http://www.perl.com/pub/2004/06/04/recorder.html?page=1#control_panel)

---

