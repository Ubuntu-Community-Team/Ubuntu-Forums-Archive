---
title: "can someone verify that LOC SRU 1.2 is broken?"
date: 2011-02-27
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-27
at the library of congress 
[http://www.loc.gov/standards/sru/specs/common.html](http://www.loc.gov/standards/sru/specs/common.html)

run this in a browser
> [http://z3950.loc.gov:7090/voyager?version=1.2&operation=searchRetrieve&query=dinosaur](http://z3950.loc.gov:7090/voyager?version=1.2&operation=searchRetrieve&query=dinosaur)

I get unsupported version in the returned XML

So far I have only been able to use version 1.1
[http://www.loc.gov/standards/sru/simple.html](http://www.loc.gov/standards/sru/simple.html)

> [http://z3950.loc.gov:7090/voyager?](http://z3950.loc.gov:7090/voyager?)
version=1.1&operation=searchRetrieve&
query=dinosaur&startRecord=2&maximumRecords=5&recordSchema=dc


what is bad is I have not using version 1.1 been able to figure out an 'and' term combining search. They all come back as 'or'
version 1.2 has info out there but nothing works

And much of the little info out there also does not work.
[http://zing.z3950.org/cql/intro.html](http://zing.z3950.org/cql/intro.html)

---

### Post by sdowney717 on 2011-02-27
following this, I discovered a way to make 'and' and 'or' work SRU1.1
also spaces need to be escaped with %20 and I know there are other chars that meed escaping
anyone else know what they are?

> //http://webcache.googleusercontent.com/search?q=cache:WdqPeEeTdosJ:srw.cheshire3.org/docs/sru-samples.html+sru+1.1+examples&cd=6&hl=en&ct=clnk&gl=us&client=ubuntu&source=www.google.com
//and terms works
$t = 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=author=%20jones%20and%20title=sword&startRecord=1&maximumRecords=20';
//or terms works
$t = 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=author=%20jones%20or%20title=sword&startRecord=1&maximumRecords=20';

$t = 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=author=%20"jones"%20and%20title="sword"or%20publisher="spirit"&startRecord=1&maximumRecords=20';
$t = 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=author=%20"jones"%20or%20publisher="spirit"&startRecord=1&maximumRecords=20';

$t = 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=author=%20"jones"%20and%20publisher="spirit"&startRecord=1&maximumRecords=20';

$t = 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=author=%20"jones"%20and%20publisher="spirit"and%20publisher="Appalachia"&startRecord=1&maximumRecords=20';

$t = 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=publisher="Catch%20the%20Spirit"&startRecord=1&maximumRecords=20';

$t = 'http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query="Catch%20the%20Spirit"&startRecord=1&maximumRecords=20';


I found out they dont support 1.2 even though their documentation suggests they do.

---

