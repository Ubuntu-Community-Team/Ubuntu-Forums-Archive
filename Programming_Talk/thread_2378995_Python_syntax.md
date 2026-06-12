---
title: "Python: syntax"
date: 2017-11-29
forum: Programming Talk
---

### Post by Drone4four on 2017-11-29
Here is a code sample from a web framework (Django) but my questions are mostly syntax-related.  Take a look at this specimen:

```

from django.shortcuts import render, get_object_or_404
from .models import Post
# Create your views here.

def home(request):
    posts = Post.objects.order_by('-pub_date')
    return render(request, 'posts/home.html', {'posts':posts})

def post_details(request, post_id):
    post = get_object_or_404(Post, pk=post_id)
    # post = Post.objects.get(pk=post_id)
    return render(request, 'posts/post_details.html',{'post':post})

```

If it helps to understand this code, [here is Atom showcasing the file tree for my Django folder](https://imgur.com/a/v0T1p).

As a beginner to python, I have a general sense of the logic and semantics of what is going on here, but there are a number of points in the code that I am left struggling with. 

**#A:** At lines 1 and 2, the script is importing external modules and functions. ‘render’ and ‘get_object_or_404’ are a specific functions inside ‘django.shortcuts’.  My question: What does the period in between ‘django’ and ‘shortcuts’ indicate? Similarly, on the next line, I get that it is the Post class being imported from ‘.models’ module, but again, what does the period mean? Similarly, line 1 from a different script, apps.py reads: ‘from django.apps import AppConfig’.  AppConfig is the function inside django.apps but isn’t using .apps redundant because it’s declared from inside the file, apps.py?

**#B:** At line 6, within the function ’home’, ‘posts’ is declared as a variable as another function, ‘order_by’ with the parameter, ‘pub_date’.  My question: Is ‘objects’ the module? If not, then what is objects? Also, ‘Post’ is the class name which was imported from .models at line 2.  But how do ‘Post’, ‘objects’ and ‘order_by’ relate to each other? I'm not sure what the periods indicate again here.

**#C:** At line 9 and line 12 for the post_details function, the ‘post’ variable is singular, where as at lines 6 and 7 for the home function, the same variable is pluralized as, ‘posts’. So I have misnamed some variables. This means the custom 404 message isn’t going to parse as intended, right?

My home.html looks like this:
```

<h1>Dobbs' Homepage Test</h1>
<h2> Latest News and Updates</h2>

{% for post in posts.all %}

<a href="{% url 'post_details' post.id %}">{{ post.title }}</a>

<br>
{{ post.pub_date_pretty }}
<br>
<img src="{{ post.image.url }}">
<br>
{{ post.summary }}
<br>
<br>
{% endfor %}

<br>

```
**#D: **Notice the references to models like ‘title’, ‘all’, ‘pub_date_pretty’ are prefixed with, ‘post’. It actually all works quite well when I run the server even through ‘post’ isn’t pluralized.  I would think all those instances should say ‘posts’ rather than post to match the directory name in my tree which is called, ‘posts’.  Why does everything work when it shouldn’t?

Thanks for your attention.

---

