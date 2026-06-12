---
title: "[SOLVED] Mimic browser action, push JS button using bash"
date: 2008-01-25
forum: Programming Talk
---

### Post by yc2 on 2008-01-25
Hello,

My ADSL service is poor and sometimes clicking the "connect-button" in my router's web-interface will resolve a broken connection. (I have a small home network incl. web-server connected to an ISP via PPPoE.) As you know one can just go to http:/192.168.1.1 and enter the USR and PWD to get into the router's pages.

I would like to do this in a script. Preferably bash that I have at least a little experience of.

If I understand correctly, what produces the button is the following code from the router (L-nksys):
```
document.write("<INPUT type=button value='"+button_value+"' onClick=Konnect(current.form,'"+button_type+"')>");
```

I have modified the code very slightly. I am not sure I can publish the entire page of code in this forum. My intention is very good and legal, but i don't think the manufacturer would like to see the entire code here. (Even though anyone who uses the router can read the code, of course.) Anyway I am not sure it is needed to see all of the code either. I have been practicing, without any good results, using cURL on the following simple java script:
```
<FORM>
<INPUT type="button" value="Change to Yellow!" name="button3" onClick="document.bgColor='yellow'">
</FORM>
```

So, I have no idea how to do it. The guides I have found on the net pertain to using cURL for entering FORM GET/POST data and I am not sure this can be readily modified into pushing a java script button of the type described above???

I have no experience of this kind of tasks. (The only remotely similar thing I have experience of was pulling out the WAN-IP number from the router with wget.) I would be very happy for suggestions how to push this java script button. My programming capacity peaked more than twenty years ago so please keep it basic ;)

Thanks a lot for guidance :KS

---

### Post by PaulFr on 2008-01-30
Have you looked at **[http://www.softwaresecretweapons.com/jspwiki/linksysrouterreanimatororsmokeandmirrorsofenterprisereliability](http://www.softwaresecretweapons.com/jspwiki/linksysrouterreanimatororsmokeandmirrorsofenterprisereliability)** as a way of automating the process ?

If not, I would think you need something like **[http://search.cpan.org/~petdance/WWW-Mechanize-1.34/lib/WWW/Mechanize.pm](http://search.cpan.org/~petdance/WWW-Mechanize-1.34/lib/WWW/Mechanize.pm)** to automate this conveniently.

HTH.

---

### Post by mssever on 2008-01-30
Because Javascript runs in the browser, you can only manipulate it if the browser provides a way to do so. As far as I know, no browser allows bash to do that.

There are two ways I can think of to accomplish your task. First, you can trace the Javascript until you discover what HTTP requests it makes, then write a script to mimic those requests. Firefox's Firebug extension would be a big help here.

The other way would be to write a Firefox extension.

I realize that neither of these approaches are in bash and both require at least a cursory familiarity with Javascript, but such is life.

---

### Post by yc2 on 2008-01-30
PaulFr & mssever

thanks a lot for supplying several approaches, I will just gradually push forward and see what I am capable of.

Taking the the GET-requests from here:
[http://www.softwaresecretweapons.com/jspwiki/linksysrouterreanimatororsmokeandmirrorsofenterprisereliability](http://www.softwaresecretweapons.com/jspwiki/linksysrouterreanimatororsmokeandmirrorsofenterprisereliability)
and using them as arguments for cURL acually works perfecly! The router can be Disconencted and Connected from a bash-script. - The author has the same router (and same problem) as I have.
```
# To disconnect router:
# curl -d  "change_action=gozila_cgi&submit_button=Status_Router&wan_proto=pppoe&submit_type=Disconnect_pppoe"   http://ROUTER_USR:ROUTER_PWD@192.168.1.1/apply.cgi
#
# To connect router:
curl -d  "change_action=gozila_cgi&submit_button=Status_Router&wan_proto=pppoe&submit_type=Connect_pppoe"   http://ROUTER_USR:ROUTER_PWD@192.168.1.1/apply.cgi
```
Now there is just left the nice little task of procucing a general surf-robot that imitates the clicks and keyboard input of the web-surfer. (And also has the ability to understand conditions.) I have heard of the program Internet Macros, but not tried it. It would maybe be useful to make something like that work under Linux?

Thanks again for really useful advice. It seems I don't even have to read the router status, just bombarding it with "Connect" does the trick.

I put "SOLVED" in the heading of this post. I don't seem to be able to edit the heading of my first post. However, I still hope this discussion can continue ...

---

### Post by mssever on 2008-01-30
> **yc2 said:**
> Now there is just left the nice little task of procucing a general surf-robot that imitates the clicks and keyboard input of the web-surfer. (And also has the ability to understand conditions.) I have heard of the program Internet Macros, but not tried it. It would maybe be useful to make something like that work under Linux?If your purpose is to ensure that your router stays connected all the time, the simplest thing would be to run your script via cron. Then, it'll just get executed every so often on a schedule you determine.

If you only want to run your script when your router loses connection, consider ping. If you make your script ping google.com, you can check its exit status (Bash's $? variable). if it's nonzero, then run your script. Again, you can either put that in cron, or make it a standalone script in a while true loop that uses sleep to control how often it runs.

> I put "SOLVED" in the heading of this post. I don't seem to be able to edit the heading of my first post. However, I still hope this discussion can continue ...The way to mark a thread as solved is to go to the Thread tools drop down at the top of the page. You'll see the option there. Bad location, I know.

---

### Post by yc2 on 2008-01-30
Thanks mssever for also supplying options to improve the approach. The ping/$?-method seems like an effort-saving way to go. (Up to now I have just used cron brutely.)

Automatised surfing is an interesting topic, I think. :) The output of the Firebug will provide interesting reading, I hope. (Or maybe far too long and complicated?) When time allows I'll definitely try it.

In the late 90's I used the Borland c++ compiler. I remember it supported "writing your own browser". I never tried that part though. Maybe such an approach is the quickest way to make a surf-robot? Still surprises me a little, that no surf-robot is readily available.

---

### Post by mssever on 2008-01-30
> **yc2 said:**
> Automatised surfing is an interesting topic, I think. :) The output of the Firebug will provide interesting reading, I hope. (Or maybe far too long and complicated?) When time allows I'll definitely try it.

In the late 90's I used the Borland c++ compiler. I remember it supported "writing your own browser". I never tried that part though. Maybe such an approach is the quickest way to make a surf-robot? Still surprises me a little, that no surf-robot is readily available.

I'm not sure that I quite understand what you mean by "surf-robot," but I think that one already exists, assembly required.

You've already discovered curl. With that tool, you can automate any HTTP request (plus others).

Example: One of my computers serves as a web server. I have a free dyndns domain name that points to my server. Of course, the address has to be kept up-to-date. My router is a Linksys WRT54G. Those routers have issues. This is the third one I've owned--my second warranty replacement. My current router refuses to update DynDNS. Then I noticed that OpenDNS had made a dynamic DNS service available. Since there were no tools that did what I wanted, I wrote my own. First, it sens a curl request to DynDNS's URL that returns the IP. (My server only knows its internal IP, of course, and the router doesn't expose any simple API for reporting the external IP.) Armed with the current IP, it checks a file to see if the address has changed. If so, it formulates a URL and sends another request to OpenDNS, which triggers OpenDNS to send the update. All I had to do to automate this surfing action was simply write a bit of Ruby code to glue the tools together.

If your "surf-robot" must live in a browser, a Firefox extension would be MUCH simpler than writing a full-blown browser. Firefox extensions can do all sorts of things, and I'm sure you could automate whatever you wanted to automate, provided you knew Firefox's version of Javascript well enough.

But my attitude is that all the necessary tools already exist for Linux. All you have to do is put them together.

---

### Post by yc2 on 2008-01-31
To me a surf-robot would be very quick and simple to use. Since there are not so many of those around, maybe there is something I haven&#8217;t thought of. I think it would receive its orders based on the page you see in the browser, not on HTML/JS. Maybe there are two ways of doing this, either trying to record, like in a macro, clicks and keyboard input. The other way would maybe be a CLI-browser (are there such?)  A browser that could accept a batch file like:

* Go to [http://google.com](http://google.com)
* Go down to the first input field, input &#8221;automatic surfing&#8221; //or other search string
* For ten downloads:
     IF the text defining a link is NOT: Cached OR Similar page OR Note THEN
        download linked page

With my slow connection it would save time to have the first ten searchresults downloaded.
   
Or 

* Go to [http://mail.google.com](http://mail.google.com)
* input my e-mail and pwd
* click &#8221;log in&#8221; button
* FOR all links:
     IF link is presented in bold font (/* unread e-mails in inbox */) THEN
       go to page and download it;

Of course I realize there are many difficulties. One must define several criteria to ensure that only e-mail and not other links are downloaded.

Maybe a surf-robot would have to put identification-tags on all links and input fields of a page, the first time you surf there? The e-mail links in Google should all appear similar in an array. These tags could later be referred to when writing the batch-script for the robot.

However, I still think the thought of a surf-robot is interesting. In software design anything is possible. Here the problem is more one of human/machine interfacing? How should one let the human, in the simplest way possible, define to the robot what actions to be taken?

OK, a lot of loose talk. However, I sometimes hope there is a simpler way to define the work-procedure for a surf-robot than going into the HTML/JS page.  I have really had to take some time to compare the GET-requests obtained from
[http://www.softwaresecretweapons.com/jspwiki/linksysrouterreanimatororsmokeandmirrorsofenterprisereliability](http://www.softwaresecretweapons.com/jspwiki/linksysrouterreanimatororsmokeandmirrorsofenterprisereliability)

with the source of
[http://192.168.1.1/Status_Router.asp](http://192.168.1.1/Status_Router.asp)

in order to understand how the GET-requests were obtained. Naturally this reflects my inexperience with Java Script . Improving my JS-experience is maybe the best way to go.

As I understand what you say: This is the simplest method. In order to automatically input data input forms, one must study the HTML/JS page in detail. Maybe this router problem is an exception? At least this router problem is easily defined on the &#8221;browser page&#8221; (the page we see in the browser when we surf): &#8221;IF there is a button labeled &#8217;Connect&#8217; THEN click it&#8221;.

I also use a Linksys WRT54GL. I use a script that works in a way similar to yours. I got my (bash) script from the Swedish Ubuntu forum. I added the following to extract the external (Wide Area Network, ISP-provided) IP from my specific router and put the IP in a file:

```
new=`wget -q http://<ROUTER_USR>:<ROUTER_PWD>@192.168.1.1/Status_Router.asp -O -| grep "var wan_ip" | sed "s/[^0-9.]//g"`
```

My Swedish DynDNS provider supplies its customers with a cURL-script that changes the IP so one can now run this script when the file &#8221;new&#8221; has changed.

So this is similar to your procedure. Ruby sounds interesting, I have not used it.

Also thanks mssever for pointing out the possibility of writing Firefox extensions, I hadn&#8217;t thought of that. I will definitely look into it.

---

### Post by mssever on 2008-01-31
I think I understand what you're talking about, now. That's something that's been available off and on in the Mac world for some time. (I grew up with Macs but haven't owned one since.) It seems to me that that would make an excellent Firefox extension, with the bonus that it would run on any platform Firefox runs on.

The problem, I think, boils down to designing a Javascript-interpreted domain-specific language (DSL) which is capable of generating Javascript. Remember, using a DSL doesn't necessarily have to involve writing code. The language could have s "click syntax" of sorts. I've never attempted a DSL before, and it strikes me as a hard problem. On the other hand, I've recently been playing with metaprogramming in Ruby, and realized that what I produced amounted to a simple DSL. So maybe the key is learning metaprogramming well. (I'm thinking as I type.)

At any rate, it does sound like an interesting project.

---

