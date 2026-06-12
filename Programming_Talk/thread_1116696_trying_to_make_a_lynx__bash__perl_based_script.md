---
title: "trying to make a lynx / bash / perl based script"
date: 2009-04-05
forum: Programming Talk
---

### Post by KhaaL on 2009-04-05
Hey all

I'm trying to write and make a script under a FOSS license to provide a service that my bank does not provide to its customers: the ability to aquire your transactions into gnucash/kmymoney. I thought this would be close to impossible until i figured out that they have a wap page - which would make things much more easier since wap pages are more simple than html.


So I thought that I'd aquire the neccesarly information with lynx, convert it with perl and later on import it with the preferred program. All of this is supposed to be done automatically. what do you think, is this a possible goal or is there an easier path?

so far i'm working with getting lynx to do my chore automatically. right now I'm having these road bumps:

[LIST]
[*]I get several errors  **SSL error:no issuer was found-Continue? (y) ** and i cant seem to find a switch to just ignore them

[*]Once logged in, swedish letters åäö does not show up but instead show up empty.

[*]I tried to use the -auth switch to login automatically, but i guess its not supposed to be used in this type of auto-logins?
[/LIST]

The command I'm using to connect is 
lynx -accept_all_cookies [https://mobilbank.swedbank.se/banking/swedbank/bvi.html?l=-1](https://mobilbank.swedbank.se/banking/swedbank/bvi.html?l=-1)

---

### Post by slavik on 2009-04-05
if you want to access web pages in perl, look at curl and lwp. Documentation is available on cpan.org, packages are in the repo.

---

### Post by KhaaL on 2009-04-05
is it easier to access pages in pern than through lynx?

(and what are curl & lwp, modules?)

---

### Post by scragar on 2009-04-05
I think libwww-mechanize-perl is a better way to access the information.
[php]
use WWW::Mechanize;

$m = WWW::Mechanize->new(stack_depth=>1, agent=>'This is the user agent string');
$m->get('URL HERE');
if( $m->success() ){
  print "The URL ".$m->uri()."
Returned Status code:".$m->status()."
And says: ".$m->content();
}
[/php]
It also handles forms [http://search.cpan.org/dist/WWW-Mechanize/lib/WWW/Mechanize.pm#FORM_METHODS](http://search.cpan.org/dist/WWW-Mechanize/lib/WWW/Mechanize.pm#FORM_METHODS)

---

### Post by ghostdog74 on 2009-04-05
> **KhaaL said:**
> is it easier to access pages in pern than through lynx?

(and what are curl & lwp, modules?)
depends on what you want to do. lynx has various commands and options for you to get web pages (eg -useragent=Name) . please read its manual to find out more.

---

