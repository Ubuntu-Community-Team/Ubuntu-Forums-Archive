---
title: "How to can I call remote RESTFull webservice using apache camel"
date: 2015-03-08
forum: Programming Talk
---

### Post by hoboy on 2015-03-08
I am trying to call a remote REST webservice using  apache camel.
I am totally new to camel I have googled but still confused.
I there an hello world of this ?
a simple example code of how to do this ?

Or a cook book like step.
in words ?

I only know the url to the RESTFull webservice 
I have to authenticated with user and password
does anybody knows how to construct the uri of RestFull service call with user/passeorword ?

---

### Post by TheFu on 2015-03-08
Is this a REST question or a Camel coding question?
REST uses HTTP - so userids and passwords **can** be sent in the normal HTTP method - if the REST interface supports that.
[http://userid:passwd@server/some-fancy-REST-URL](http://userid:passwd@server/some-fancy-REST-URL)

Of course, the authentication used by any REST service can be something else.

I know nothing about Camel. Sorry.  Coding questions probably belong in the develment forum - might be good to label the language too ... Camel seems to be a module for Java ... expected since Apache has gone over to the "Dark Side" in recent years.

---

### Post by hoboy on 2015-03-08
> **TheFu said:**
> Is this a REST question or a Camel coding question?
REST uses HTTP - so userids and passwords **can** be sent in the normal HTTP method - if the REST interface supports that.
[http://userid:passwd@server/some-fancy-REST-URL](http://userid:passwd@server/some-fancy-REST-URL)

Of course, the authentication used by any REST service can be something else.

I know nothing about Camel. Sorry.  Coding questions probably belong in the develment forum - might be good to label the language too ... Camel seems to be a module for Java ... expected since Apache has gone over to the "Dark Side" in recent years.

Thanks very much it is a bought RESt and camel question
it is rest used in camel.

---

