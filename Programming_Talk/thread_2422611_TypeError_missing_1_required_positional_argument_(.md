---
title: "TypeError: missing 1 required positional argument (word counter Django app)"
date: 2019-07-10
forum: Programming Talk
---

### Post by Drone4four on 2019-07-10
I&#8217;ve got a Python script which counts and prints the number of words in a text file. The script runs beautifully. It takes a public domain book (a text file such as Alice and Wonderland) which then counts the top 10 most used words (but which also filters out stopwords).  [See here for some of my previous work](https://stackoverflow.com/questions/56436291/filtering-stop-words-out-of-a-large-text-file-using-package-nltk-corpus).

Now I am trying to &#8216;port&#8217; this Python shell script to Django. My intention for this project is to have the Django app count the number of words in a blog post. But for now I&#8217;m still using Alice and Wonderland in .txt format.

I&#8217;ve encountered some issues with my local dev server running but serving me a series of name errors involving my views module when I navigate to the url. I was hoping some of you could provide some insight.

When I run the server and navigate to `http://127.0.0.1:8000/seth/`, this is the error showing  in my web browser pointing to the issue at hand:  [https://pastebin.com/raw/52x2c4iN](https://pastebin.com/raw/52x2c4iN)

Here is the traceback from my local Django dev server in my shell: [https://pastebin.com/raw/a8PTcRki](https://pastebin.com/raw/a8PTcRki)

The file with the most problems is my **counters/views.py **(current app only): 

```
from django.http import HttpResponse, HttpResponseRedirect
from django.shortcuts import render
from collections import Counter
from nltk.corpus import stopwords
import re
# from .forms import UploadFileForm
from django.views.generic.edit import FormView
from .forms import FileFieldForm

text = None
word = None

class FileFieldView(FormView):
    form_class = FileFieldForm
    template_name = 'seth.html'  # Replace with your template.
    success_url = 'seth_success' # Replace with your URL or reverse().

    def post(self, request, *args, **kwargs):
        form_class = self.get_form_class()
        form = self.get_form(form_class)
        files = request.FILES.getlist('Alice.txt')
        if form.is_valid():
            for f in files:
                global text
                # Do something with each file. For example the following? Is what follows even valid?
                text = f.read().lower()                
            return self.form_valid(form)
        else:
            return self.form_invalid(form)

def counters(request, text):
    """
    This function processes the top 10 most common words and then renders them.
    """
    stoplist = stopwords.words('english')
    stoplist.extend(["said","gutenberg", "could", "would",]) 
    clean = []
    global word
    global count
    for word in re.split(r"\W+",text):
        if word not in stoplist:
            clean.append(word)
    top_10 = Counter(clean).most_common(10)
    for word,count in top_10:
        return render(request, 'counters/seth.html', {'word': word, 'count': count})

def main(request):
    """
    This function calls the counters function
    """
    text = FileFieldView.post()
    run = counters(text)

if __name__ == "__main__":
    main()
    pass

```

I realize that the problem is with the way the text variable is tossed around. I probably should not be invoking global variables as I do at lines 24, 38, 39 in my views model (above). Furthermore, out of the Udemy course material I&#8217;ve watched and in the official Django docs I&#8217;ve read, I&#8217;ve never seen a views.py which uses main() for calling functions. I realize I am sort of departing from Django norms here. What might you people recommend I try instead?

Here is **counters/models.py**:

```
from django.db import models
from django import forms
import datetime

class UploadFileForm(forms.Form):
    title = forms.CharField(max_length=150)
    file = forms.FileField()

class Count(models.Model):
    title = models.CharField(max_length=161)
    pub_date = models.DateTimeField()
    image = models.ImageField(upload_to='media/')
    body = models.TextField()
    now = datetime.datetime.now()

class FileFieldForm(forms.Form):
    file_field = forms.FileField(widget=forms.ClearableFileInput(attrs={'multiple': True}))
```

Here is **counters/forms.py**:

```
# With advice from this Django doc: [https://docs.djangoproject.com/en/2.2/topics/http/file-uploads/](https://docs.djangoproject.com/en/2.2/topics/http/file-uploads/)
 
from django import forms

class UploadFileForm(forms.Form):
    title = forms.CharField(max_length=50)
    file = forms.FileField()

class FileFieldForm(forms.Form):
    file_field = forms.FileField(widget=forms.ClearableFileInput(attrs={'multiple': True}))
```

Here is **urls.py** in parent project directory: 

```
from django.contrib import admin
from django.urls import path, re_path
# from . import views
from posts.views import *
from redactors.views import *
from counters.views import *
from AllAbove.views import *
from django.conf.urls.static import static
from django.conf import settings

urlpatterns = [
   path('admin/', admin.site.urls),
   path('', home, name='home'),
   path('result/', result, name='result'),
   path('seth/', counters, name='seth'),
   #path('james/', post_details, name='james'),
   path('maggie/', maggie_post_details, name='maggie'),
   path('AllAbove/', all_above, name='AllAbove'),
   re_path(r'^posts/(?P<post_id>[0-9]+)/$', post_details, name='james'),
   path('simon/', redactors, name='simon'),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT) + static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
```

Here is Alice and Wonderland [in .txt format](https://github.com/Angeles4four/CC_Redact_Iter2/blob/v1.2/counters/Alice.txt)

What other comments might you have about my code, in particular the views.py shared above?

I&#8217;m running Django 2.2 and Python 3.7.

Pull requests on GitHub ([my repo can be found here](https://github.com/Angeles4four/CC_Redact_Iter2/tree/v1.2)) are welcome although I realize if asking for pull requests like this might not be reasonable for most of you but I thought I&#8217;d ask anyways, just in case a kind and generous forum contributor has time on their hands. Requirements.txt is included on the master branch.

For what it is worth, here is some of the documentation I&#8217;ve been working with.

I&#8217;ve referred to official Django docs for:
[list]
[*][File uploads](https://docs.djangoproject.com/en/2.2/topics/http/file-uploads/)
[*][Form handling with class-based views](https://docs.djangoproject.com/en/2.1/topics/class-based-views/generic-editing/)
[*][HttpRequest.FILES](https://docs.djangoproject.com/en/2.2/ref/request-response/#django.http.HttpRequest.FILES)
[/list]
Stack Overflow questions I&#8217;ve used:
[list]
[*][What does the if __name__ == "__main__": do?](https://stackoverflow.com/questions/419163/what-does-if-name-main-do) 
[*][reverse for success_url on Django Class Based View complain about circular import](https://stackoverflow.com/questions/31275574/reverse-for-success-url-on-django-class-based-view-complain-about-circular-import) 
[*][How can I get uploaded text file in view through Django?](https://stackoverflow.com/questions/39436612/how-can-i-get-uploaded-text-file-in-view-through-django) 
[*][How can i get the file name from request.FILES?](https://stackoverflow.com/questions/3111779/how-can-i-get-the-file-name-from-request-files)
[*][How to reverse_lazy to a view/url with variable?](https://stackoverflow.com/questions/46184193/how-to-reverse-lazy-to-a-view-url-with-variable) 
[/list]

---

### Post by norobro on 2019-07-10
[SIZE=2]The following comments are from eyeballing the code that you have posted. It'll be tomorrow, if then, before I have time to download and run your app. 

The error is because you are calling counters() from url.py and it is expecting two parameters. If you want to call main you need to change this line:```
path('seth/', counters, name='seth'),
```Don't know if there are any repercussions from calling main() but I believe it will need to return HttpResponse().

The following returns to the caller after one iteration:```
    for word,count in top_10:
        return render(request, 'counters/seth.html', {'word': word, 'count': count})
```Try something like this:
 ```
#    for word,count in top_10:
     return render(request, 'counters/seth.html', {'top_10': top_10})
```Then in your template:```
{% for word, count in top_10 %}
    {{word}} {{count}} <br>
{% endfor %}
```


Post back with any progress that you make. HTH[/SIZE]

---

### Post by Drone4four on 2019-07-10
Thank you, **@norobro**! This helps. 

I managed to eliminate the TypeError and 'positional argument' issue. Alls I did was remove my silly global variable declarations and then change my function inside my views.py to look like this

```
def counters(request, text="")
```

This eliminates the error that I discussed originally. No more trackback. 

But to achieve what I intend, you are right that I will need to include your three additional suggestions.  I'll play around with these changes tomorrow. I'll report back here as soon as I can.

Thanks for your help so far, **@norobro**. :D

---

### Post by Drone4four on 2019-07-11
I&#8217;ve made a few changes based on your suggestions.  [Here]("https://github.com/Angeles4four/CC_Redact_Iter2/tree/v1.3") are my latest changes in my GitHub repo. I talk through and discuss my changes below. 

> **norobro said:**
> The following returns to the caller after one iteration:

```
    for word,count in top_10:
        return render(request, 'counters/seth.html', {'word': word, 'count': count})
```

Try something like this:
```
#    for word,count in top_10:
     return render(request, 'counters/seth.html', {'top_10': top_10})
```


I made this change. My counters function looks like this:

```
def counters(request, text=""):
   """
   This function processes the top 10 most common words and then renders them.
   """
   stoplist = stopwords.words('english')
   stoplist.extend(["said","gutenberg", "could", "would",])
   clean = []
   for word in re.split(r"\W+",text):
       if word not in stoplist:
           clean.append(word)
   top_10 = Counter(clean).most_common(10)
   # for word,count in top_10:
   return render(request, 'counters/seth.html', {'top_10': top_10})

```

As you can see near the bottom there, the for loop has been commented out. Now this function just returns the request, the template location, and specifies the top_10 variable as a key-value pair.

My template was rather basic. I hadn&#8217;t put much thought into it yet. So this was a great suggestion:

> **norobro said:**
> Then in your template:
```
{% for word, count in top_10 %}
    {{ word }} {{ count }}  <br>
{% endfor %}
```


I agree that this makes a lot more sense for my &#8216;seth&#8217; template. I transferred it over into my code.

When I run the server, there are no errors in the shell. There&#8217;s no 404 or traceback either. When navigating to the &#8216;seth&#8217; page, the output shows simply: &#8220;1&#8221;. See here: 

[img]https://i.imgur.com/NqBhuqb.jpg[/img]

Then I went back and attempted to integrate your first suggestion by changing the function reference in urls.py. You suggested:
> **norobro said:**
> The error is because you are calling counters() from url.py and it is expecting two parameters. If you want to call main you need to change this line:```
path('seth/', counters, name='seth'),
```Don't know if there are any repercussions from calling main() but I believe it will need to return HttpResponse().

So I changed the view function reference from &#8216;counters' to &#8216;main&#8217; so that line looks like this now: path('seth/', main, name='seth').  

Now I am getting a NameError and TypeError depending on line 48 inside my view where I declare the text variable. Inside my main() function, I attempt to call the FileFieldView class and post method (which is present earlier above in this particular view). Here is my original line with the text declaration inside main:
```
text = FileFieldView.post(request)
```
I tried these two as well (in addition to a few others):
```
text = FileFieldView(self).post(request, text)
```
```
text = FileFieldView(request).post(self, text)
```
The shell raises: "NameError: name 'self' is not defined". I am struggling with grasping the basic concept of how to call instances of classes properly in this context.

I&#8217;ve begun reviewing: 
[LIST]
[*]Dan Bader&#8217;s &#8220;[Python's Instance, Class, and Static Methods Demystified]("https://realpython.com/instance-class-and-static-methods-demystified/#class-methods")&#8221;
[*]w3school&#8217;s &#8220;[Python Classes and Objects]("https://www.w3schools.com/python/python_classes.asp")&#8221; 
[*]freeCodeCamp&#8217;s terrific guide: &#8220;[Let&#8217;s get classy: how to create modules and classes with Python]("https://www.freecodecamp.org/news/lets-get-classy-how-to-create-modules-and-classes-with-python-44da18bb38d1/")&#8221;
[/LIST]

---

### Post by norobro on 2019-07-11
G'day Drone4four. 

Just for grins comment out the FileFieldView.post() call in main and add the following line to counters:```
    """
    This function processes the top 10 most common words and then renders them.
    """
    text = open("counters/Alice.txt", "r").read().lower()    [COLOR=#ff0000]# add this line[/COLOR]
    stoplist = stopwords.words('english')
```
I'm not clear about your ultimate goal. Are you planning to put the word count on a blog page? Or a separate page? What is the purpose of the FileFieldView class?

---

### Post by Drone4four on 2019-07-12
> **norobro said:**
>  Just for grins comment out the FileFieldView.post() call in main and add the following line to counters:```
    """
    This function processes the top 10 most common words and then renders them.
    """
    text = open("counters/Alice.txt", "r").read().lower()    [COLOR=#ff0000]# add this line[/COLOR]
    stoplist = stopwords.words('english')
```



That worked, my friend!!

[img]https://i.imgur.com/V4a8AN8.jpg[/img]

Thank you for your help and guidance so far, **@norobro**.

To answer your questions:

**[SIZE=4][COLOR="#FF0000"]Short answer:[/COLOR][/SIZE]**: 
> I'm not clear about your ultimate goal. Are you planning to put the word count on a blog page? Or a separate page? 
In short, first on a separate page, then inside a blog post.

> What is the purpose of the FileFieldView class?
As I explain below, the purpose of the FileFieldView class was to collect a file uploaded by the author of the blog.  But this is just a stepping stone until I figure out how to re-direct the class method to analyze the content of the blog post instead of the uploaded text file.

**[SIZE=4][COLOR="#FF0000"]Long answer:[/COLOR][/SIZE]**.

To elaborate in greater detail, in terms of the purpose and end-goal of my project, it&#8217;s intended to become a website which showcases three different learn-to-code opportunities:
[LIST=1]
[*]Process a fake credit card number entered by the user which then &#8216;redacts&#8217; the first 12 of 16 digits of the input. 
[*]Create a rudimentary blog. But my finished product will only show a single blog post. It&#8217;s **not** intended to show multiple posts. It&#8217;s **not** going to be used to publish posts regularly (like typical blogs are used for). There will be only one post.
[*]Wirte a word counter (inside an HTML table) embedded as part of the blog post.
[/LIST]
I&#8217;ve started out by writing these three features separately, in individual apps. Once all three run as intended, eventually I&#8217;ll assemble and consolidate all of them into a single template which will appear as the home/landing page of my website. This is my ultimate goal, to answer your question.

I&#8217;ve completed the first two learning opportunities. To complete the third learning task, I&#8217;ve broken it down into three sub-objectives:
[LIST=a]
[*]Write a feature which processes a text file provided in the app&#8217;s source code directory. The output shows on an isolated, separate web page (for now). With your help, **@norobro**, this sub-task is now completed!
[*]Take that feature to the next step by processing a text file uploaded by the user (from the Django admin dashboard) for the blog post. I had intended on achieving this by using Django&#8217;s &#8220;[FileFieldView]("https://docs.djangoproject.com/en/2.2/topics/http/file-uploads/#uploading-multiple-files")&#8221; class. This is why I included the FileFieldView form.  However after taking a closer look today at this File Uploads Django doc, since I don't need to upload multiple files, maybe all I need is a simple form containing the more basic &#8220;[FileField]("https://docs.djangoproject.com/en/2.2/topics/http/file-uploads/#basic-file-uploads")&#8221; view leveraging the section of the Django doc titled &#8220;[Handling uploaded files with a model]("https://docs.djangoproject.com/en/2.2/topics/http/file-uploads/#handling-uploaded-files-with-a-model")&#8221;
[*]Finally, I intend on rewiring this app to process or count the words in the contents of the one (and only) blog post and have the word counter embedded within that post
[/LIST]

---

