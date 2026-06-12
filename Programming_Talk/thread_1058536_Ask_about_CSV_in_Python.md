---
title: "Ask about CSV in Python"
date: 2009-02-02
forum: Programming Talk
---

### Post by vietwow on 2009-02-02
Hi all,

In Python, I have variable contains a string like this :

> {uid: -1
 script_name: /mp3
 end_execution_time: 1233634440
 client_address: 192.168.0.24
 request_time: 1233634441
 sql_count: 2
 stat_execution_time: 1233634440
 mem_usage: -260720
 sever_host: mp3.baihat.com
 request_method: GET
 sever_pot: 80
 extra_data: ale ale
 sever_addr: 192.168.0.2
 sql_execution_time: 15
 productName: Video
 referer: None
 request_uri: /mp3/nghe-bai-hat/Dung-bo-cuoc-Than-Moc-Du-Dong-Y2J.IWZFZI0U.html
 session_id: pd4op8if3n0mupg36ggs9ld147
 la_userName: none
 page_session: 791b44f47859cf55fe1b21c7a649e22a
 user_agent: Mozilla/5.0 (compatible; Googlebot/2.1; +[http://www.google.com/bot.html](http://www.google.com/bot.html))
 quey_string:
 session_name: PHPSESSID}


Now I need to write this string into a CVS file using Python

How can I do this ?

Thanx

---

### Post by dominiquec on 2009-02-02
Suggestion: read it in line by line, parse at the colon, just keep the parametr.  The CSV might look something like:

> -1,/mp3,1233634440,192.168.0.24,2....

I assume that because it's CSV, it'll be some form of tabular data and you'll have many more instances like it.

Is this what you want to do?

---

### Post by vietwow on 2009-02-03
> **dominiquec said:**
> Suggestion: read it in line by line, parse at the colon, just keep the parametr.  The CSV might look something like:



I assume that because it's CSV, it'll be some form of tabular data and you'll have many more instances like it.

Is this what you want to do?

Dear dominiquec,

Actually, I want to get both each pair of value into CSV (a pair is seperated by colon like this :

uid -1
script_name /mp3
client_address 192.168.0.24
...

Because, after that, I will use other program to get data from this CSV file, and example when I get :

uid -1

Ah, I know that value "-1" is belong to "uid" property
and more ....

Thanx

---

### Post by myrtle1908 on 2009-02-03
Not knowing Python very well, in Perl this is how you *could* do it.  Perhaps it will point you in the right direction, perhaps not.

I couldn't understand exactly how you wanted your CSV so the solution I've  posted assumes you wanted it like:-

```
uid -1,script_name /mp3,end_execution_time 1233634440,...
```

There are however flaws with this.  What if a comma exists in one of the values?  Are you sure this is what you wanted? 

Anyhoo ...

```
use strict;
use warnings;

my @s;
while (<DATA>) {
	if ($_ =~ m/\{?(\w+)\s*\:(.*?)\}?$/) {
		push @s, $1 . $2;
		
	}
}

print join(',', @s);

__DATA__
{uid: -1
script_name: /mp3
end_execution_time: 1233634440
client_address: 192.168.0.24
request_time: 1233634441
sql_count: 2
stat_execution_time: 1233634440
mem_usage: -260720
sever_host: mp3.baihat.com
request_method: GET
sever_pot: 80
extra_data: ale ale
sever_addr: 192.168.0.2
sql_execution_time: 15
productName: Video
referer: None
request_uri: /mp3/nghe-bai-hat/Dung-bo-cuoc-Than-Moc-Du-Dong-Y2J.IWZFZI0U.html
session_id: pd4op8if3n0mupg36ggs9ld147
la_userName: none
page_session: 791b44f47859cf55fe1b21c7a649e22a
user_agent: Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
quey_string:
session_name: PHPSESSID}
```

Yields:-
```
uid -1,script_name /mp3,end_execution_time 1233634440,client_address 192.168.0.24,request_time 1233634441,sql_count 2,stat_execution_time 1233634440,mem_usage -260720,sever_host mp3.baihat.com,request_method GET,sever_pot 80,extra_data ale ale,sever_addr 192.168.0.2,sql_execution_time 15,productName Video,referer None,request_uri /mp3/nghe-bai-hat/Dung-bo-cuoc-Than-Moc-Du-Dong-Y2J.IWZFZI0U.html,session_id pd4op8if3n0mupg36ggs9ld147,la_userName none,page_session 791b44f47859cf55fe1b21c7a649e22a,user_agent Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html),quey_string,session_name PHPSESSID
```

---

### Post by vietwow on 2009-02-03
> **dominiquec said:**
> Suggestion: read it in line by line, parse at the colon, just keep the parametr.  The CSV might look something like:



I assume that because it's CSV, it'll be some form of tabular data and you'll have many more instances like it.

Is this what you want to do?

Dear dominiquec,

After review my project, I decide do what you decribe, means  CSV look like :

-1,/mp3,1233634440,192.168.0.24,2.... 

So How can I dow this with Python ?


@myrtle1908 : Thank you ver much but I only need a python solution, anyway thanx

---

### Post by myrtle1908 on 2009-02-03
The following almost works.  I can't for the life of me figure out why 'session_name: PHPSESSID' is included in the last match.  Could someone please explain.

[PHP]import re

s = """{uid: -1
script_name: /mp3
end_execution_time: 1233634440
client_address: 192.168.0.24
request_time: 1233634441
sql_count: 2
stat_execution_time: 1233634440
mem_usage: -260720
sever_host: mp3.baihat.com
request_method: GET
sever_pot: 80
extra_data: ale ale
sever_addr: 192.168.0.2
sql_execution_time: 15
productName: Video
referer: None
request_uri: /mp3/nghe-bai-hat/Dung-bo-cuoc-Than-Moc-Du-Dong-Y2J.IWZFZI0U.html
session_id: pd4op8if3n0mupg36ggs9ld147
la_userName: none
page_session: 791b44f47859cf55fe1b21c7a649e22a
user_agent: Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
quey_string:
session_name: PHPSESSID}"""

p = re.compile('^.*?:\s*(.*?)}?$', re.M);
l = p.findall(s)

print ','.join(l)[/PHP]

Yields:-

```
-1,/mp3,1233634440,192.168.0.24,1233634441,2,1233634440,-260720,mp3.baihat.com,GET,80,ale ale,192.168.0.2,15,Video,None,/mp3/nghe-bai-hat/Dung-bo-cuoc-Than-Moc-Du-Dong-Y2J.IWZFZI0U.html,pd4op8if3n0mupg36ggs9ld147,none,791b44f47859cf55fe1b21c7a649e22a,Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html),session_name: PHPSESSID
```

---

### Post by vietwow on 2009-02-03
Dear myrtle1908,

You code is work very good but when I include it into my code, it don't work perfect :

```
        data=simplejson.JSONDecoder().decode(m.get(Qname))
        a=str(data)
        a = a.replace("'","")
        a = a.replace('{',' ')
        s = a.replace('}','')
        print s + "\n" + "\nAfter process : \n"
        p = re.compile('^.*?:\s*(.*?)}?$', re.M);
        l = p.findall(s)
        print ','.join(l)
```


output of this :

```
[root@server root]# ./script.py
 uid: -1, script_name: /mp3, end_execution_time: 1233650030, client_address: 66.249.73.11, request_time: 1233650033, sql_count: 2, start_execution_time: 1233650030, mem_usage: -618780, server_host: mp3.baihat.com, request_method: GET, server_port: 80, extra_data: ale ale, server_addr: 192.168.0.2, sql_execution_time: 15, productName: Video, referer: None, request_uri: /mp3/search/Niu-Keo-Them-Don-Dau.html, session_id: nt534gk55e5cba5gt5r9g6n9j0, la_userName: none, page_session: 255770fc246e037bdea1eb76efb042f4, user_agent: Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html), query_string: , session_name: PHPSESSID

After process :

-1, script_name: /mp3, end_execution_time: 1233650030, client_address: 66.249.73.11, request_time: 1233650033, sql_count: 2, start_execution_time: 1233650030, mem_usage: -618780, server_host: mp3.baihat.com, request_method: GET, server_port: 80, extra_data: ale ale, server_addr: 192.168.0.2, sql_execution_time: 15, productName: Video, referer: None, request_uri: /mp3/search/Niu-Keo-Them-Don-Dau.html, session_id: nt534gk55e5cba5gt5r9g6n9j0, la_userName: none, page_session: 255770fc246e037bdea1eb76efb042f4, user_agent: Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html), query_string: , session_name: PHPSESSID
```

It just process first pair (uid : -1  => -1), all other pair still old

How can I fix this ?

Thanx

---

### Post by myrtle1908 on 2009-02-03
I see.  So you don't actually have a multi-line string as your source data.  This is what was inferred by your original post.

As stated before, my Python skills are lax and I now note that you are dealing with a JSON string.

If you show me what 's' looks like I can probably help but I'm guessing there is a better way to produce a CSV (with Python) given your source data is already JSON encoded.

---

