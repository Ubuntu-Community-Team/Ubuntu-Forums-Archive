---
title: "Django field model for HTML parser?"
date: 2017-11-14
forum: Programming Talk
---

### Post by Drone4four on 2017-11-14
The contents of my models.py looks like this:
```

from django.db import models

# Create your models here.
class Post(models.Model):
        title = models.CharField(max_length=256)
        pub_date = models.DateTimeField()
        image = models.ImageField(upload_to='media/')
        body = models.TextField()

        def __str__(self):
            return self.title

        def pub_date_pretty(self):
            return self.pub_date.strftime('%A %d %B %Y @ %-I:%M:%S %p')

        def summary(self):
            return self.body[:350]

```

Lines 5 through 8 initiate the model class variables for my blog dashboard.  My dashboard [looks like this](https://imgur.com/a/HTffL).  There is a title, pub date, image and body.  The Udemy instructor suggests consulting [the official Django doc for field types/options](https://docs.djangoproject.com/en/1.11/ref/models/fields/). I’m not sure I really understand most of it.  There is just so much information there.  My question for all of you: Which field option or field type initiates an HTML parser for body text?  I mean, when I go to to create a new blog post, how do I create rich text with HTML formatting buttons like bold, underline and italics?  It’s not really the buttons I care about.  I just want my HTML tags to parse. Take note of the HTML tags [I’ve circled in red here](https://imgur.com/a/wV4qs).  How do I get the h5, hr and em to parse? Is there a field option/type for this? I don’t see it in the models fields doc.

Thanks for your attention.

---

### Post by RIchard James13 on 2017-11-25
Django renders the models fieldtype via a Widget. So there is a URL widget and a email widget but there is no WYSIWYG widget. The best solution would be to use a widget that someone else has created as programming such a thing is no easy task.

Here are some widgets you could try.
[http://django-tinymce.readthedocs.io/en/latest/]("http://django-tinymce.readthedocs.io/en/latest/")
[https://github.com/django-ckeditor/django-ckeditor]("https://github.com/django-ckeditor/django-ckeditor")

---

