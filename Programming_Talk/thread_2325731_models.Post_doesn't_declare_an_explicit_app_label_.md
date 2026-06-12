---
title: "models.Post doesn't declare an explicit app_label  and either isn't in an application"
date: 2016-05-24
forum: Programming Talk
---

### Post by zerop2 on 2016-05-24
/home/martin/Downloads/site1/site1/reg/models.py:37: RemovedInDjango19Warning: 
Model class site1.reg.models.Post doesn't declare an explicit app_label 
and either isn't in an application in INSTALLED_APPS or else was imported 
before its application was loaded. This will no longer be supported in Django 1.9.
  class Post(models.Model):




i had already added 'site1.reg.models.Post' to MIDDLEWARE_CLASSES but still have error


INSTALLED_APPS = (
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'django.contrib.sites',
)


MIDDLEWARE_CLASSES = (
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.auth.middleware.SessionAuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
    'django.middleware.security.SecurityMiddleware',
    'site1.reg.models.Post',
)


registration.html


{% block content %}


    <h1>New user registration</h1>


    <form method="POST" class="post-form">{% csrf_token %}


        {{ form.as_p }}


        <button type="submit" class="save btn btn-default" >Save</button>


    </form>


{% endblock %}


urls.py


from django.conf.urls import include, url


from . import views






urlpatterns = [


    url(r'^reg/$', views.post_new, name='post_new'),


    url(r'^reg/(?P<pk>\d+)/$', views.post_detail, name='post_detail'),


]


views.py


from .forms import PostForm


from django.shortcuts import render


from django.template.loader import get_template






def post_new(request):


    form = PostForm()


    return render(request, 'registration.html', {'form': form})






def post_detail(request, pk):


    post = get_object_or_404(Post, pk=pk)


    if request.method == "POST":


        form = PostForm(request.POST, instance=post)


        if form.is_valid():


            post = form.save(commit=False)


            post.author = request.user


            post.ProjectName = request.ProjectName


            post.UserName = request.UserName


            post.Company = request.Company


            post.Contact = request.Contact


            post.InitialPassword = request.InitialPassword


            post.UserType = request.UserType


            post.BusinessType = request.BusinessType


            post.published_date = timezone.now()


            post.save()


            return redirect('registration.html', pk=post.pk)


    else:


        form = PostForm(instance=post)




    return render(request, 'registration.html', {'form': form})


models.py


from django.db import models


from django.utils import timezone
from django.apps import AppConfig


import csv
import os.path


USERTYPE = (  
    ('Cyberport Tenant', 'Cyberport Tenant'),
    ('SmartSpace User', 'SmartSpace User'),
    ('Cyberport Incubate', 'Cyberport Incubate'),
    ('Collaboration Center Subscriber', 'Collaboration Center Subscriber'),
    ('Cyberport Alumnus', 'Cyberport Alumnus'),
    ('Technology Partner', 'Technology Partner'),
    ('HKOSUG', 'HKOSUG'),
    ('Others', 'Others'),
)




BUSINESSTYPE = (  
    ('Building', 'Building'),
    ('Data Analysis', 'Data Analysis'),
    ('Digital Entertainment', 'Digital Entertainment'),
    ('Education', 'Education'),
    ('Games', 'Games'),
    ('Gaming', 'Gaming'),
    ('ICT', 'ICT'),
    ('Marketing', 'Marketing'),
    ('Social Media', 'Social Media'),
    ('Others', 'Others'),
)




class MyAppConfig(AppConfig):
    name = 'src.my_app_label'


    def ready(self):
        post_migrate.connect(do_stuff, sender=self)




class Post(models.Model):


    author = models.ForeignKey('auth.User')


    Email = models.CharField(max_length=70)
    ProjectName = models.CharField(max_length=70)
    UserName = models.CharField(max_length=70)
    Company = models.CharField(max_length=70)
    Contact = models.CharField(max_length=70)
    InitialPassword = models.CharField(max_length=70)
    UserType = models.CharField(max_length=30, choices=USERTYPE)
    BusinessType = models.CharField(max_length=30, choices=BUSINESSTYPE)
    #UserType = models.ChoiceField(choices=USERTYPE, required=True )
    #BusinessType = models.ChoiceField(choices=BUSINESSTYPE, required=True )


    #ProjectName = models.TextField()


    created_date = models.DateTimeField(default=timezone.now)


    published_date = models.DateTimeField(blank=True, null=True)






    def publish(self):


        self.published_date = timezone.now()
        isexist = os.path.isfile('newusers.csv') 
        with open('/home/martin/Downloads/site1/site1/reg/newusers.csv', 'a') as csvfile:
          fieldnames = ['name','email address','project','initial password','userType','contact','businessType','company']
          writer = csv.DictWriter(csvfile, fieldnames=fieldnames)
          if isexist == false:
             writer.writeheader()
          writer.writerow({'name': UserName, 'email address': Email, 'project': ProjectName, 'initial password': InitialPassword,'userType': UserType, 'contact': Contact, 'businessType': BusinessType, 'company': Company,})




        self.save()






    def __str__(self):


        return self.title


forms.py


from django import forms






from .models import Post




USERTYPE = (  
    ('Cyberport Tenant', 'Cyberport Tenant'),
    ('SmartSpace User', 'SmartSpace User'),
    ('Cyberport Incubate', 'Cyberport Incubate'),
    ('Collaboration Center Subscriber', 'Collaboration Center Subscriber'),
    ('Cyberport Alumnus', 'Cyberport Alumnus'),
    ('Technology Partner', 'Technology Partner'),
    ('HKOSUG', 'HKOSUG'),
    ('Others', 'Others'),
)




BUSINESSTYPE = (  
    ('Building', 'Building'),
    ('Data Analysis', 'Data Analysis'),
    ('Digital Entertainment', 'Digital Entertainment'),
    ('Education', 'Education'),
    ('Games', 'Games'),
    ('Gaming', 'Gaming'),
    ('ICT', 'ICT'),
    ('Marketing', 'Marketing'),
    ('Social Media', 'Social Media'),
    ('Others', 'Others'),
)






class PostForm(forms.ModelForm):






    #if form.is_valid():


     #post = form.save(commit=False)


     #post.author = request.user


     #post.published_date = timezone.now()


     #post.save()m


    class Meta:


        model = Post


        fields = ('Email', 'ProjectName', 'UserName', 'Company', 'Contact', 'InitialPassword','UserType','BusinessType')
	#fields = ('title', 'text',)
        UserType = forms.ChoiceField(choices=USERTYPE, required=True )
        BusinessType = forms.ChoiceField(choices=BUSINESSTYPE, required=True )

---

