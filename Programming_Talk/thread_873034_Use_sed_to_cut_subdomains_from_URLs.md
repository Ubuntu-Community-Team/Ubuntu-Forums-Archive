---
title: "Use sed to cut subdomains from URLs"
date: 2008-07-28
forum: Programming Talk
---

### Post by pytheas22 on 2008-07-28
I have some URLs that look like:

```
ad4.rtm-1.vip.rm.ac4.yahoo.com
[www.04.01.snc1.facebook.com](www.04.01.snc1.facebook.com)
iad.llnw.net
```

and I'd like to use sed (unless there's a better tool...maybe awk, but I don't know as much about it) to cut out all of the subdomain stuff.  In other words, I want sed to return:
```

yahoo.com
facebook.com
llnw.net
```

I know I can cut out everything from the beginning of the string to the last period ( . ) with a command like:
```

sed -e 's/^.*\.//'
```

and that I could tell it to stop at a certain period with something like:

```
sed -e 's/^.*\.//1'
```

but what I really need to tell it is, "match everything up to the second-to-last period in the string."  I'm sure there's an easy way to do this, but I can't figure it out after some reading.  Does anyone know?

---

### Post by mssever on 2008-07-28
The way I'd write that regexp in Ruby is:
```
url.gsub(/^.*([^.]+\.[^.]+)$/, '\1')
```I'm not too familiar with sed's peculiarities, but you should be able to write the regexp to capture what you want, and return only that backreference.

The algorithm you requested might be insufficient, however, depending on your data. For example, google.com isn't a subdomain, but neither is google.co.uk or google.com.au (or my old school's domain, tvi.cc.nm.us). So if you're needing a generic algorithm, counting dots is sure to give some incorrect results.

---

### Post by drubin on 2008-07-28
what about 2nd level domains? ie
```
google.co.za
```

---

### Post by geirha on 2008-07-28
This sed should take care of the first case, but not the case rubinboy mentions.
```
$ sed -r 's/.*\.([^.]+\.[^.]+)$/\1/' << EOF
ad4.rtm-1.vip.rm.ac4.yahoo.com
www.04.01.snc1.facebook.com
iad.llnw.net
EOF
yahoo.com
facebook.com
llnw.net

```

I think awk is better for the second case. I'm no expert on awk, but this should do the trick I think.
```
$ awk -F. '{ 
if ($(NF-1) == "co") printf $(NF-2)"."; 
printf $(NF-1)"."$(NF)"\n";
}' << EOF
ad4.rtm-1.vip.rm.ac4.yahoo.com
www.04.01.snc1.facebook.com
iad.llnw.net
google.co.za
EOF
yahoo.com
facebook.com
llnw.net
google.co.za

```

---

### Post by mssever on 2008-07-28
> **geirha said:**
> I think awk is better for the second case. I'm no expert on awk, but this should do the trick I think.
This code works by explicitly handling a special case. So google.co.za and google.co.uk will work, but not someschool.ac.uk or someschool.k12.tx.us. You have to handle the rules for every TLD (top-level domain) that can possibly occur in your input, and different TLDs have different rules. Some (such as com, net, org, nl, ca, de, etc.) are simple and fit the OP's approach. Others (such as uk, au, za, etc.) require an additional domain before the "actual" domain. Still others have varying rules. For example, I own scottseverance.us, which follows the same rules as .com. But schools often have domains of the form <school name>.<school type>.<state abbreviation>.us (e.g., tvi.cc.nm.us). But you can't assume that if you have, e.g., nm.us that you'll always have an additional qualifier, because most state governments own and operate state.<state abbreviation>.us (e.g., state.nm.us).

So this problem is more complex than it might appear on the surface.

---

### Post by siouzi on 2008-07-28
This problem quickly escalates into a major one. A valid approach would probably be to query nameservers etc... to get the proper domain name.

Here's something that can be used. Although in perl, it can be quickly converted into php/python/ruby etc... All validation code has been removed to keep this simple and readable. Also, this may already be outdated...

```

#!/usr/bin/perl -w
use strict;

# prints example.com
printf "%s\n", get_domain('example.com');
printf "%s\n", get_domain('www.example.com');

# prints example.tokyo.jp
printf "%s\n", get_domain('www.example.tokyo.jp');

# prints example.a.se
printf "%s\n", get_domain('sweden.is.a.nice.country.example.a.se');

# etc...

# The get_domain DOES NOT verify the validity of the input. It expects a valid
# hostname, not an IP address, not anything else, so beware...
#
# Sources:
# - Wikipedia
# - http://www.tellinya.com/read/2007/10/16/191.html and
#   http://www.tellinya.com/read/2007/12/06/255.html
#
use constant COUNTRY_SLDS => <<SLDS;
com.ac edu.ac gov.ac mil.ac net.ac org.ac ac.ae co.ae com.ae gov.ae net.ae
org.ae pro.ae sch.ae com.ai edu.ai gov.ai org.ai com.ar edu.ar gov.ar int.ar
mil.ar net.ar org.ar ac.at co.at gv.at or.at priv.at act.au asn.au com.au
conf.au csiro.au edu.au gov.au id.au id.au info.au net.au nsw.au org.au otc.au
oz.au qld.au sa.au tas.au telememo.au vic.au wa.au com.az net.az org.az com.bb
net.bb org.bb ac.be belgie.be dns.be fgov.be com.bh edu.bh gov.bh net.bh org.bh
com.bm edu.bm gov.bm net.bm org.bm adm.br adv.br agr.br am.br arq.br art.br
ato.br bio.br bmd.br cim.br cng.br cnt.br com.br coop.br ecn.br edu.br eng.br
esp.br etc.br eti.br far.br fm.br fnd.br fot.br fst.br ggf.br gov.br imb.br
ind.br inf.br jor.br lel.br mat.br med.br mil.br mus.br net.br nom.br not.br
ntr.br odo.br org.br ppg.br pro.br psc.br psi.br qsl.br rec.br slg.br srv.br
tmp.br trd.br tur.br tv.br vet.br zlg.br com.bs net.bs org.bs ab.ca bc.ca gc.ca
mb.ca nb.ca nf.ca nl.ca ns.ca nt.ca nu.ca on.ca pe.ca qc.ca sk.ca yk.ca co.ck
edu.ck gov.ck net.ck org.ck ac.cn ah.cn bj.cn com.cn cq.cn edu.cn gd.cn gov.cn
gs.cn gx.cn gz.cn hb.cn he.cn hi.cn hk.cn hl.cn hn.cn jl.cn js.cn ln.cn mo.cn
net.cn nm.cn nx.cn org.cn qh.cn sc.cn sh.cn sn.cn sx.cn tj.cn tw.cn xj.cn xz.cn
yn.cn zj.cn arts.co com.co edu.co firm.co gov.co info.co int.co mil.co nom.co
org.co rec.co store.co web.co au.com br.com cn.com de.com eu.com gb.com hu.com
no.com qc.com ru.com sa.com se.com uk.com us.com uy.com za.com ac.cr co.cr ed.cr
fi.cr go.cr or.cr sa.cr com.cu net.cu org.cu ac.cy com.cy gov.cy net.cy org.cy
co.dk art.do com.do edu.do gob.do gov.do mil.do net.do org.do sld.do web.do
art.dz ***.dz com.dz edu.dz gov.dz net.dz org.dz pol.dz com.ec edu.ec fin.ec
gov.ec med.ec mil.ec net.ec org.ec com.ee fie.ee med.ee org.ee pri.ee com.eg
edu.eg eun.eg gov.eg net.eg org.eg sci.eg com.er edu.er gov.er ind.er mil.er
net.er org.er com.es edu.es gob.es nom.es org.es biz.et com.et edu.et gov.et
info.et name.et net.et org.et ac.fj com.fj gov.fj id.fj org.fj school.fj ac.fk
com.fk gov.fk net.fk nom.fk org.fk aeroport.fr assedic.fr asso.fr avocat.fr
avoues.fr barreau.fr cci.fr chambagri.fr com.fr gouv.fr greta.fr medecin.fr
nom.fr notaires.fr pharmacien.fr port.fr prd.fr presse.fr tm.fr veterinaire.fr
com.ge edu.ge gov.ge mil.ge net.ge org.ge pvt.ge ac.gg alderney.gg co.gg gov.gg
guernsey.gg ind.gg ltd.gg net.gg org.gg sark.gg sch.gg com.gr edu.gr gov.gr
net.gr org.gr com.gt edu.gt gob.gt ind.gt mil.gt net.gt org.gt com.gu edu.gu
gov.gu mil.gu net.gu org.gu com.hk edu.hk gov.hk idv.hk net.hk org.hk agrar.hu
bolt.hu casino.hu city.hu co.hu erotica.hu erotika.hu film.hu forum.hu games.hu
hotel.hu info.hu ingatlan.hu jogasz.hu konyvelo.hu lakas.hu media.hu news.hu
org.hu priv.hu reklam.hu sex.hu shop.hu sport.hu suli.hu szex.hu tm.hu tozsde.hu
utazas.hu video.hu ac.id co.id go.id mil.id net.id or.id ac.il co.il gov.il
idf.il muni.il net.il org.il ac.im co.im gov.im net.im nic.im org.im ac.in co.in
ernet.in firm.in gen.in gov.in ind.in mil.in net.in nic.in org.in res.in ac.ir
co.ir gov.ir id.ir net.ir org.ir sch.ir ac.je co.je gov.je ind.je jersey.je
ltd.je net.je org.je sch.je com.jo edu.jo gov.jo mil.jo net.jo org.jo ac.jp
ad.jp aichi.jp akita.jp aomori.jp chiba.jp co.jp ed.jp ehime.jp fukui.jp
fukuoka.jp fukushima.jp gifu.jp go.jp gov.jp gr.jp gunma.jp hiroshima.jp
hokkaido.jp hyogo.jp ibaraki.jp ishikawa.jp iwate.jp kagawa.jp kagoshima.jp
kanagawa.jp kanazawa.jp kawasaki.jp kitakyushu.jp kobe.jp kochi.jp kumamoto.jp
kyoto.jp lg.jp matsuyama.jp mie.jp miyagi.jp miyazaki.jp nagano.jp nagasaki.jp
nagoya.jp nara.jp ne.jp net.jp niigata.jp oita.jp okayama.jp okinawa.jp or.jp
org.jp osaka.jp saga.jp saitama.jp sapporo.jp sendai.jp shiga.jp shimane.jp
shizuoka.jp takamatsu.jp tochigi.jp tokushima.jp tokyo.jp tottori.jp toyama.jp
utsunomiya.jp wakayama.jp yamagata.jp yamaguchi.jp yamanashi.jp yokohama.jp
com.kh edu.kh gov.kh mil.kh net.kh org.kh per.kh ac.kr co.kr go.kr kyonggi.kr
ne.kr or.kr pe.kr re.kr seoul.kr com.kw edu.kw gov.kw net.kw org.kw com.la
net.la org.la com.lb edu.lb gov.lb mil.lb net.lb org.lb com.lc edu.lc gov.lc
net.lc org.lc asn.lv com.lv conf.lv edu.lv gov.lv id.lv mil.lv net.lv org.lv
com.ly net.ly org.ly ac.ma co.ma net.ma org.ma press.ma com.mk com.mm edu.mm
gov.mm net.mm org.mm com.mn edu.mn gov.mn museum.mn org.mn com.mo edu.mo gov.mo
net.mo org.mo com.mt edu.mt net.mt org.mt tm.mt uu.mt com.mx edu.mx gob.mx
net.mx org.mx com.my edu.my gov.my net.my org.my alt.na com.na cul.na edu.na
net.na org.na telecom.na unam.na com.nc net.nc org.nc de.net gb.net uk.net ac.ng
com.ng edu.ng gov.ng net.ng org.ng sch.ng com.ni edu.ni gob.ni net.ni nom.ni
org.ni tel.no com.np edu.np gov.np net.np org.np fax.nr mob.nr mobil.nr
mobile.nr tel.nr tlf.nr ac.nz co.nz cri.nz geek.nz gen.nz govt.nz iwi.nz
maori.nz mil.nz net.nz org.nz parliament.nz school.nz ac.om biz.om co.om com.om
edu.om gov.om med.om mod.om museum.om net.om org.om pro.om dk.org eu.org ac.pa
com.pa edu.pa gob.pa net.pa org.pa sld.pa com.pe edu.pe gob.pe mil.pe net.pe
nom.pe org.pe ac.pg com.pg net.pg com.ph mil.ph net.ph ngo.ph org.ph biz.pk
com.pk edu.pk fam.pk gob.pk gok.pk gon.pk gop.pk gos.pk gov.pk net.pk org.pk
web.pk agro.pl aid.pl art.pl atm.pl auto.pl bialystok.pl biz.pl com.pl edu.pl
gda.pl gmina.pl gsm.pl info.pl katowice.pl krakow.pl lodz.pl lublin.pl mail.pl
media.pl miasta.pl mil.pl net.pl nieruchomosci.pl nom.pl olsztyn.pl org.pl pc.pl
powiat.pl poznan.pl priv.pl radom.pl realestate.pl rel.pl sex.pl shop.pl
sklep.pl slupsk.pl sos.pl szczecin.pl szkola.pl targi.pl tm.pl torun.pl
tourism.pl travel.pl turystyka.pl waw.pl wroc.pl zgora.pl edu.ps gov.ps plo.ps
sec.ps com.pt edu.pt gov.pt int.pt net.pt nome.pt org.pt publ.pt com.py edu.py
net.py org.py com.qa edu.qa gov.qa net.qa org.qa asso.re com.re nom.re arts.ro
com.ro firm.ro info.ro nom.ro nt.ro org.ro rec.ro store.ro tm.ro www.ro com.ru
gov.ru net.ru org.ru pp.ru com.sa edu.sa gov.sa med.sa net.sa org.sa pub.sa
sch.sa com.sb edu.sb gov.sb net.sb org.sb com.sd edu.sd gov.sd med.sd net.sd
org.sd sch.sd bd.se brand.se fh.se fhsk.se fhv.se komforb.se kommunalforbund.se
komvux.se lanarb.se lanbib.se mil.se naturbruksgymn.se org.se parti.se pp.se
press.se sshn.se tm.se com.sg edu.sg gov.sg net.sg org.sg per.sg com.sh edu.sh
gov.sh mil.sh net.sh org.sh co.st com.st consulado.st edu.st embaixada.st gov.st
mil.st net.st org.st principe.st saotome.st store.st com.sv edu.sv gob.sv org.sv
red.sv com.sy gov.sy net.sy org.sy ac.th co.th go.th net.th or.th com.tn
edunet.tn ens.tn fin.tn gov.tn ind.tn info.tn intl.tn nat.tn net.tn org.tn
rnrt.tn rns.tn rnu.tn tourism.tn bbs.tr com.tr edu.tr gen.tr gov.tr mil.tr
net.tr org.tr aero.tt at.tt au.tt be.tt biz.tt ca.tt co.tt com.tt coop.tt de.tt
dk.tt edu.tt es.tt eu.tt fr.tt gov.tt info.tt int.tt it.tt jobs.tt mobi.tt
museum.tt name.tt net.tt nic.tt org.tt pro.tt se.tt travel.tt uk.tt us.tt co.tv
com.tw edu.tw gov.tw idv.tw net.tw org.tw com.ua edu.ua gov.ua net.ua org.ua
ac.ug co.ug go.ug or.ug ac.uk co.uk edu.uk gov.uk ltd.uk me.uk mod.uk net.uk
nhs.uk nic.uk org.uk plc.uk police.uk sch.uk dni.us fed.us com.uy edu.uy gub.uy
mil.uy net.uy org.uy arts.ve bib.ve co.ve com.ve edu.ve firm.ve gov.ve info.ve
int.ve mil.ve net.ve nom.ve org.ve rec.ve store.ve tec.ve web.ve co.vi net.vi
org.vi ac.vn biz.vn com.vn edu.vn gov.vn health.vn info.vn int.vn name.vn net.vn
org.vn pro.vn ch.vu com.vu de.vu edu.vu fr.vu net.vu org.vu com.ws edu.ws gov.ws
net.ws org.ws com.ye edu.ye gov.ye mil.ye net.ye org.ye ac.yu co.yu edu.yu
org.yu ac.za agric.za alt.za bourse.za city.za co.za edu.za gov.za law.za mil.za
net.za ngo.za nis.za nom.za org.za school.za tm.za web.za ac.zw co.zw gov.zw
org.zw
SLDS

sub get_domain {
    my $hostname = lc shift or return;

    # Split the hostname
    my @parts = split /\./, $hostname;

    # Hostname is the domain when there are only two parts (example.com)
    return $hostname if scalar @parts == 2;

    # Grab domain, second level domain and top level domain from the end of
    # the parts list
    my ( $domain, $sld, $tld ) = @parts[ -3 .. -1 ];

    # Country specific SLD exceptions
    # Sweden: .se has a or b or ... z.se
    return "$domain.$sld.$tld" if $tld eq 'se' && $sld =~ /^[a-z]$/;

    # check all others...
    return "$domain.$sld.$tld" if COUNTRY_SLDS =~ m{\b$sld\.$tld\b}sx;

    # OK, the 3 part is probably not part of the domain, leaving just sld, tld
    return "$sld.$tld";
}

```

---

### Post by geirha on 2008-07-28
> **mssever said:**
> This code works by explicitly handling a special case. So google.co.za and google.co.uk will work, but not someschool.ac.uk or someschool.k12.tx.us. You have to handle the rules for every TLD (top-level domain) that can possibly occur in your input, and different TLDs have different rules. Some (such as com, net, org, nl, ca, de, etc.) are simple and fit the OP's approach. Others (such as uk, au, za, etc.) require an additional domain before the "actual" domain. Still others have varying rules. For example, I own scottseverance.us, which follows the same rules as .com. But schools often have domains of the form <school name>.<school type>.<state abbreviation>.us (e.g., tvi.cc.nm.us). But you can't assume that if you have, e.g., nm.us that you'll always have an additional qualifier, because most state governments own and operate state.<state abbreviation>.us (e.g., state.nm.us).

So this problem is more complex than it might appear on the surface.

Indeed. I didn't bother to check how many different types of such second-level (or x-level) domains there was, but I had a feeling there were quite a few more than just the co. However, in case the OP does not need to take into account all such domains, I gave solutions on the samples given in the thread.

---

### Post by mssever on 2008-07-28
> **siouzi said:**
> This problem quickly escalates into a major one. A valid approach would probably be to query nameservers etc... to get the proper domain name.This wouldn't really help, since DNS doesn't know what a domain name is in the way the OP is using the term. x.y.z.co.uk is a perfectly valid domain name as far as DNS is concerned, but the OP presumably wants just z.co.uk.

> Here's something that can be used. Although in perl, it can be quickly converted into php/python/ruby etc... All validation code has been removed to keep this simple and readable. Also, this may already be outdated...It's incomplete since it doesn't properly handle the us TLD.

Here's another case: Suppose I run the blog somecoolblog.blogspot.com. The proper domain name isn't blogspot.com; it's somecoolblog.blogspot.com. This suggests that this problem might be impossible to solve algorithmically.

---

### Post by pytheas22 on 2008-07-28
Lots of interesting points; thanks for all of the ideas.
> 
A valid approach would probably be to query nameservers etc... to get the proper domain name.

I initially tried something along these lines, but have hundreds of URLs to parse, and it can take a long time waiting on DNS servers for each one.
> 
Here's another case: Suppose I run the blog somecoolblog.blogspot.com. The proper domain name isn't blogspot.com; it's somecoolblog.blogspot.com. This suggests that this problem might be impossible to solve algorithmically.

This is also a good point and is especially relevant to my purposes, which I maybe should have described in more detail earlier:

I need to monitor the Internet activity on one of my computers for parental-control reasons.  I installed iptraf to keep a log of all sites visited, and it works well, but the iptraf log is hard to understand for non-geeks (and a non-geek is the one who wants to know which sites are being visited on the machine in question).

So I wrote a bash script that parses the iptraf log and prints out each site visited and a link to it, along with a timestamp, into an html file.  The result can be viewed nicely in Firefox, but the one problem is that some of the URLs that are getting logged, like ad4.rtm-1.vip.rm.ac4.yahoo.com, don't lead to valid sites.  Although all of us know that ad4.rtm-1.vip.rm.ac4.yahoo.com is owned by yahoo (ad server?), that's apparently not obvious to non-geeks, who get confused when they click the link and end up at a weird site that doesn't mention yahoo anywhere.  So that's why I wanted to get rid of all of the subdomain stuff.

But it's a good point that in a lot of cases, cutting out the subdomain either won't work or will link to a site that doesn't give much information about what content originally viewed.  So I may just have to accept that it's not going to be possible to do this well without a lot of tedious work tracking down all the possible different kinds of cases.

Also, I notice in mssever's signature that he or she has written a program to do a very similar thing to what I am trying, so I'll look into that.  Maybe it's just what I need.

Thanks again for all of the responses.

---

### Post by mssever on 2008-07-29
> **pytheas22 said:**
> Also, I notice in mssever's signature that he or she has written a program to do a very similar thing to what I am trying, so I'll look into that.  Maybe it's just what I need.
Thanks for mentioning iptraf. I didn't know about that program, but it looks useful. You might be interested in checking out urlsnarf, which is what I use with Net Responsibility. Both iptraf and urlsnarf have their limitations, but the limitations are different, so they might work well together.

I suppose you've noticed that this kind of logging results in a staggering amount of data to sift through. Currently, Net Responsibility tends to present the accountability partner with too much information. A web interface is in the works (but not ready yet) that should be a major improvement.

The reason I'm mentioning this is that my plan for the web interface might provide a useful solution for you, as well. I log full URLs sorted by domain. The web interface will maintain a user-configurable whitelist and blacklist. Domains on the whitelist will be hidden on the theory that they've already been determined to be OK. Domains on the blacklist will be displayed very prominantly because they've been explicitly determined to be problematic. Both lists will allow wildcards, so *.google.com will also match [www.google.com](www.google.com) and mail.google.com (I'm not sure yet what syntax I'll use for wildcards, but this is the general idea).

So, if Net Responsibility doesn't work out for you, a blacklist/whitelist system might be a reasonable compromise.

---

### Post by pytheas22 on 2008-07-29
I ended up using the perl script provided by siouzi (did you write that yourself?) for snipping the URLs down.  It works pretty well, and if I need to know more information about a visited site than the snipped URL provides, I can always go back to the iptraf logs to find the original URL in its entirety.
> 
A web interface is in the works (but not ready yet) that should be a major improvement.

Interesting ideas...what is the web frontend being written in?  If you're using PHP I could try to help if you're in need of it (unfortunately I don't really know any web languages besides PHP).  Will users need Apache for this?

I was going to have my script create an html file daily with pages visited for only that day, which would help to keep the URL list manageable.  But it would be great to have a frontend where users could configure better what they want to see.

Anyway, I installed net-responsibility and will take a look at its features and concepts (by the way, have you thought about putting an amd64 .deb of the stable release on the site?  It would make the software more accessible to more people).

---

### Post by mssever on 2008-07-29
> **pytheas22 said:**
> Interesting ideas...what is the web frontend being written in?  If you're using PHP I could try to help if you're in need of it (unfortunately I don't really know any web languages besides PHP).  Will users need Apache for this?I'm planning to write it in Python, using the Django framework. I'm trying to get away from PHP, since the more I use it, the less I like it. Plus, I'm planning to host it on Google App Engine, which requires that I use Python. Since this will be a web service, there'll be nothing for the users to install (other than Net Responsibility, of course). Any help is welcome; I could especially use graphic design help.

> By the way, have you thought about putting an amd64 .deb of the stable release on the site?  It would make the software more accessible to more people.
Try the SVN version. I only recently figured out how to make EPM generate platform-independant packages. I could definitely use help from someone with packaging experience to re-work my build system. Ideally, there should be some sort of generic installer (setup.rb maybe), and then the package should be debianized separately. Right now, Net Responsibility is tied fairly closely to *buntu; I don't know how well it'll build on other distros (since I don't use any other distros).

---

### Post by pytheas22 on 2008-07-29
Your installer builds an amd64 .deb fine (using the code that I checked out yesterday); I was just thinking that it would be easier to provide a .deb available for immediate download.  For me it's not a problem to run the install script, deal with missing dependencies, build a .deb and install it with dpkg, but I think that for a lot of 64-bit users who are intimidated by command-line work, it would be easier to have a .deb that could be installed with one download and one click.  I'll the package that I built yesterday here.

I don't know if the installer would be smart enough to grab missing dependencies for the amd64 .deb (since when I built it, I had already been forced to install all of the dependencies), but it might, and I'm sure that if it's not, there's a way to fix it.  Unfortunately I don't know much about packaging.
> 
I'm planning to write it in Python, using the Django framework.

I don't know much about Python but took a class for it once and can write some basic stuff.  If you have written any code so far for the web stuff, is it available anywhere?

Finally, here is my finished script in case it's ever useful to anyone else:
```

#!/bin/bash

#this script parses the iptraf log at /var/log/iptraf/ip_traffic-1.log and displays sites visited and a time stamp for each visit.  It is designed to be run once a day (at midnight) as a cronjob and to create an html file logging activity for that day.

###set how the date should be displayed (it will be used as the file name for each day's log).
date=$(date --date='1 day ago' '+%a %b %d 20%y') ###we offset the day by 1, because the cronjob runs at midnight to process the previous day's (that is, the day that ended at 23:59:59) iptraf logs.

###parse the log file and dump relevant lines into a text file, 'traffic'

grep -o -e '[MonTueWedThuFriSatSun].*:www' /var/log/iptraf/ip_traffic-1.log | sed 's/ [TCPUDP].*from//' | sed 's/family.*to //' | sed 's/:www//' > traffic

###write information from 'traffic' into an html file, 'traffic.html'

echo "<h1>Internet activity for $date</h1>" > "logs/$date.html"

exec < traffic
while read line
do
###if we have URLs, not IP addresses, to parse (and therefore need to remove subdomains)
	if !(echo $line | grep '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}') then ./parse_domain.pl $line | sed -e 's/ / <a href="http:\/\/'/5 | sed -e 's/$/">/' | awk '{print $1,$2,$3,$4,$5,$6,$7,$7}' | sed -e 's/$/<\/a><br \/>/' | sed -e 's/ href="http:\/\///2' | sed -e 's/">//2' >> "logs/$date.html"

###for just IP addresses (we could resolve the IPs too using "host" or "dig," but DNS responses are slow)
	else echo $line | sed -e 's/ / <a href="http:\/\/'/5 | sed -e 's/$/">/' | awk '{print $1,$2,$3,$4,$5,$6,$7,$7}' | sed -e 's/$/<\/a><br \/>/' | sed -e 's/ href="http:\/\///2' | sed -e 's/">//2' >> "logs/$date.html"
	fi
done

###remove ip_traffic-1.log, since it gets very big quickly, and restart iptraf daemon, because it seems to be flaky sometimes and dies after a while
rm -f traffic
rm -f /var/log/iptraf/ip_traffic-1.log*
killall iptraf
iptraf -i all -B
```

My script works for now, but I will continue to play around with your code, as the features are much richer.

---

### Post by mssever on 2008-07-29
> **pytheas22 said:**
> Your installer builds an amd64 .deb fine (using the code that I checked out yesterday); I was just thinking that it would be easier to provide a .deb available for immediate download.Which version are you talking about? I believe that's fixed in SVN, but I've got a couple other changes to complete before I do another release.

> I don't know much about Python but took a class for it once and can write some basic stuff.  If you have written any code so far for the web stuff, is it available anywhere?It'll probably be in SVN eventually, but I haven't started coding it yet.

---

### Post by pytheas22 on 2008-07-30
> Which version are you talking about? I believe that's fixed in SVN, but I've got a couple other changes to complete before I do another release.

On your sourceforge page [here]("http://sourceforge.net/project/platformdownload.php?group_id=205710"), you have a 32-bit .deb available, as well as an .rpm and a source tarball, but there's no 64-bit .deb; if you want one, you have to download the source and build the .deb yourself.  Maybe it would be easier for non-advanced users to have an amd64 .deb available for immediate download from the sourceforge page.  It's not a big deal, just a suggestion.

---

### Post by mssever on 2008-07-30
> **pytheas22 said:**
> On your sourceforge page [here]("http://sourceforge.net/project/platformdownload.php?group_id=205710"), you have a 32-bit .deb available, as well as an .rpm and a source tarball, but there's no 64-bit .deb; if you want one, you have to download the source and build the .deb yourself.  Maybe it would be easier for non-advanced users to have an amd64 .deb available for immediate download from the sourceforge page.  It's not a big deal, just a suggestion.
OK, so you're talking about the latest release. That's already been fixed in SVN and the change will be reflected in the next release.

---

