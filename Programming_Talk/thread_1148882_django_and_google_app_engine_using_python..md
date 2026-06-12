---
title: "django and google app engine using python."
date: 2009-05-04
forum: Programming Talk
---

### Post by hockey97 on 2009-05-04
HI, I am experienced wtih php. I havent' really have experience using python for web developing. 


Ok, what I have to do is count how many clicks occurred on a rotating ad system.

My idea was to put in the html file a <a> tag with href  and have that link to be the link where it would direct the request to the python function.I would have a hidden input type and a from in the html file. I want to pass variable values through a form that won't accept user input but have input of variables and those variable values would be connected to another python function that will  pass on the ad graphic url and the website url.the website url will be passed to the 1st function ( the one I talked about at the start of this paragraph.

the python function would then grab this url then do a database query 

grab the record then update the count field and add 1 or increment(++)

then it will return a redirect function that has the url input into it.

Then it redirects the user to the website of that ad that was on our site.



How can you do this?  this would be in python and it uses google app engine and django.

if you know of any good referances that I can look not google apps engine  or django docs.

I already looked into it and I can't figure out how to use the functions.

I did read on httpResponseRedirect function that supposed to redirect the user to a website.

So any resources or any help I would appreciate it.

---

### Post by sloggerkhan on 2009-05-04
I'd set up a url conf for /ads/<ad_id>/
where ad_id is the id or name of whatever the add in question is, and you have the appropriate django regex matching for, to send as an argument to your veiw function for the ad.

Then have a view function that has ad_id as an argument, gets an ad object by ad_id, which is a unique field for ad_id objects, and increments it's views count (integer field) by 1, then redirects to the advertiser website. 

I'd probably itegrate a django imagefield into the ad object model, also.
That way you can use a template that uses ad objects, and can do something where {{obj.[name of imagefield]}} is a link to /ads/{{obj.ad_id}} within your site.


Shouldn't be too hard, but if you don't know the basics of django, you will probably find it confusing.

---

### Post by hockey97 on 2009-05-04
well, how would I redirect a user. I mean what code would I use to redirect a user to a website.

I looked at the django docs and saw HttpRespondRedirect('url') 

is that right? and is that all I need to do to redirect a user to a website.

I mean I would use return HttpRespondRedirect('url')   the url is a variable that holds the value of the website url.

for me django and google apps engine is confusing. I am more comfortable with php.

The reason I have to use django and python etc is because I had to do it for work. They use google servers because it's free to an extent.

I am using google apps engine with django.

I use datastore for the database.

---

### Post by loell on 2009-05-04
for redirect.

it's just ```
self.redirect("/home")

```

it should be inside a class with

```
(webapp.RequestHandler):
```

---

### Post by hockey97 on 2009-05-04
I am not sure if we use webapp.

would that code be in django?

sorry. I am new to django and googles app engine. 

I am not experienced with python. I only made a small calculator with python that is about it and it was just for learning purposes.

I didn't have time to finish up learning python. 

so the self. code  I wouldn't need to make self an argument for the function?

---

### Post by loell on 2009-05-04
yeah, that method is native to app engine and not with django

to use it, you must import webapp class

```
from google.appengine.ext import webapp
```

for me personally, i just use app engine directly and not layer it with django.  django might come in handy, that.. if you are familiar with it. 
if not, then might as well just code it with app engine classes. 

does django really a requirement for your web app?

---

### Post by loell on 2009-05-04
more info on GAE redirect.

[http://code.google.com/appengine/docs/python/tools/webapp/redirects.html]("http://code.google.com/appengine/docs/python/tools/webapp/redirects.html")

---

### Post by hockey97 on 2009-05-04
ok, just 2 more question. Would this code be able to redirect people to a full url?

Like [http://www.google.com](http://www.google.com)  or is this just a redirect with the website url.

Like you can only redirect the user anywhere on your site only.

Also can I pass variables from html files to views.py by a form that has nothing but hidden input types.

I just want to pass the ads url to the function in views.py so when the person clicks on the ad it will direct them to the url which calls on that function in views.py so it will count the click and add 1 to clicks field in the database.

basicly I am making a links click counter.  I have variables passed from database to the html file and want to store them back in a form  hidden and pass that variable back to the views.py to the function tha will process it and add 1 to the number of click the ad links had. Then once it counts  the click it then will redirect the user to the ads website.
thats the goal.

Thanks for the replies.

---

### Post by loell on 2009-05-04
it can take full URI or relative URI like the one above.

and any types of forms can be processed, 

[http://code.google.com/appengine/docs/python/gettingstarted/handlingforms.html]("http://code.google.com/appengine/docs/python/gettingstarted/handlingforms.html")

---

### Post by hockey97 on 2009-05-05
ok, what I have done so far  is : 


a file name contex.py  is the one that passes values to a html file.

so I made python functions to pass from the database to the html files values. I passed the urls and ads graphic urls  to the html file.

The ads url is thrown from contex.py to the html file which is in a form that has a input type hidden. I gave it a name is ad , adl , adr. 

I have 3 areas to display 3 different ads. 

Now this hidden input type. I want to toss these urls which are the real ads urls to  views.py functions. I setup a urls.py which are the urls that would transfer the request to those functions in views.py 

now when they get passed. THe functions in views.py will grab those urls.

Then do a query for those records and then add 1 to the clicks filed.

Then it will return the person to a http redirect to that ads website.

This basicly is supposed to be a click per link counter.

I get the values from the form that has hidden inputs by using respons.post.

I am using the post method.

Currently it seems to not work.

I wanted to make sure if  httpResponseRedirect would accept a variable that has a url assigned to it.


Thanks for the help.

---

### Post by hockey97 on 2009-05-05
ok, I have the form that has a hidden field. but no submit button.

I just notice I need to have a submit button to pass vairables.

So I ask how can I pass the url from the html file to views.py?

I mean the data is coming from context.py where it passes the variable to the html file. I then need to pass on that value to views.py.

I thought I could make a form that will automaticly pass on hidden fields.

So I need a way to pass variables to views.py.

---

### Post by sloggerkhan on 2009-05-06
You need to do some basic django tutorials.
It will be a lot easier to pass a value as an argument through regular expression filter in the url than by doing hidden forms, though you could do either. In any case, the questions you are asking give me the impression that you haven't really explored how Django is intended to work. (For example, you shouldn't need to use a file named contex.py, you should be able to include all your basic code within the normal django project and app files.)

---

### Post by hockey97 on 2009-05-07
the website is already made. The previous programmer has the stuff setup.

So I am following what he told me. 

He basically wants it to be seperate. 


what I found out after googling around. I found this: 
```
  url(r'^(?P<key>.*)/$', 'click', name='ad-click') 
```

I was told that is how you pass a variable from the html file to views.py.

I did look at the tutorials of django. The problem is that the previous programmer created some python code and made modifications. 

So the structure is more organized. Basicly one file will be the views.py 

then any file that needs to throw data to the html file will be in a different file which in this case is  contex.py 

then for what I am doing now I have to add a ad/ views.py  this would be the code that will grab the variable values from the html and then process it. 

The functions would only run when the user clicks the link.

I got rid of the forms with hidden values. I am going this route.

I am still trying to understand this fully. I am reading up on it by googling it.

I found the django tutorials and docs confusing. I mean I do understand but I never found a tutorial on passing variables values from a html file.

They only showed how to grab it from a form in a html fille. 

it's with the request.POST['something']  type command

I also tried looking at the urls patterns area.

well I am off to explore on google.

---

### Post by sloggerkhan on 2009-05-07
[http://docs.djangoproject.com/en/dev/topics/http/urls/](http://docs.djangoproject.com/en/dev/topics/http/urls/)
[http://docs.djangoproject.com/en/dev/intro/tutorial03/](http://docs.djangoproject.com/en/dev/intro/tutorial03/)
should help some.

Pretty much by putting codes in the links, you can have django process those codes as arguments to a function through the use of regex.

So you could, for (ugly) example, have a template with

```

<a href=http://mysite.com/{{random-ad-id}}><img src={{random-ad}}/></a>

```

where the view function for that template chooses a random ad, then passes the random-ad and random-ad-id arguments to the template, one being the proper path for displaying the ad-image and the other an ad-id code. The ad id code is used at part of a url to your site for ad processing.

When you click on the image, the random-ad-id is interpreted by urls.py as an argument to the view function that [http://mysite.com](http://mysite.com) directs to.

So in views.py you'd have something like:
```

def addclick(request, ad-id):
   a = Ads.objects.get(addid=ad-id)
   a.addClick() # custom method for adding a click count or whatnot
# or in your case, maybe:
   import contex
   contex.func(ad-id)
   return HttpResponseRedirect(a.addSourceUrl)
 
```

Note that urls.conf would be mapping along line of:
```

(r'^(?P<ad-id>\w+)/$', 'mymodule.views.addclick')

```


Honestly, your posts and descriptions are so unclear I have trouble understanding you.

---

