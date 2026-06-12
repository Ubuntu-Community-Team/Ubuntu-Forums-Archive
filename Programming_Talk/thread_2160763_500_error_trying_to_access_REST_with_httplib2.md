---
title: "500 error trying to access REST with httplib2"
date: 2013-07-08
forum: Programming Talk
---

### Post by wordjuggler on 2013-07-08
Hi,
 

 Have been trying to access a rest API using httplib2 – seems whatever I do I get a 500 response. I am a beginner so the problem may well be the result of something I'm doing (or not doing). Any pointers would be appreciated. Here is my latest attempt:

```
import httplib2
http = httplib2.Http()

username = 'MyUsername'
password = 'MyPassword'

http.add_credentials(username, password)

response, content = http.request('https://infoconnect1.highwayinfo.govt.nz/ic/jbi/TREIS/REST/FeedService/')

print response, content
```

And this is what I get in response:

```
{'status': '500', 'transfer-encoding': 'chunked', 'set-cookie': 'JSESSIONID=BF90C53A0550A80481AC4C9580C3A2D8.jvm1; Path=/ic', 'connection': 'close', 'date': 'Mon, 08 Jul 2013 09:57:40 GMT', 'content-type': 'text/xml'} <?xml version='1.0' encoding='UTF-8'?><Fault><faultcode>Server</faultcode><faultstring>An expected request parameter [username] was not found or is empty.</faultstring></Fault>


 
```

Cheers,
Blair

---

