---
title: "Python or Ruby???"
date: 2005-12-30
forum: Programming Talk
---

### Post by j-a-p on 2005-12-30
Hello people,

I have recently started learning programming.  I played about with a couple of languages, namely C++ and Ruby.

I think C++ is a little heavy going for me at the moment, so I've left that one out for a bit.  I like Ruby very much as it seems easy to get along with and was considering sticking with it.

I want to learn a language that I can use for anything, be it console apps, gui apps, web apps or system stuff.  I know this is probably a bit of a dream, so I'll settle for the nearest thing.  I particularly want the language I go for to be good for shell scripting and web apps.

So I am now unsure which one to go with from my shortlist of Ruby or Python.  
I know all is possible with both of these, but to be honest I am confused as to which packages to use.

For example, I know ruby has Rails for building dynamic websites which looks great, it can be used for shell scripting and  gui apps.  Which package do I use for the gui apps.  Also what is the future looking like for Ruby?

For Python, from which I gather is very popular with ubuntu users I was overwhelmed with which way to go when building web apps.  I've had some experience with ASP which seemed easy just embedding the ASP in HTML.  What is the equivalent with python?

Someone put me on the right track please.

---

### Post by knowmad on 2005-12-30
Even though its not one of the options, my vote is for perl!

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=j-a-p]Hello people,

I have recently started learning programming.  I played about with a couple of languages, namely C++ and Ruby.

I think C++ is a little heavy going for me at the moment, so I've left that one out for a bit.  I like Ruby very much as it seems easy to get along with and was considering sticking with it.

I want to learn a language that I can use for anything, be it console apps, gui apps, web apps or system stuff.  I know this is probably a bit of a dream, so I'll settle for the nearest thing.  I particularly want the language I go for to be good for shell scripting and web apps.

So I am now unsure which one to go with from my shortlist of Ruby or Python.  
I know all is possible with both of these, but to be honest I am confused as to which packages to use.

For example, I know ruby has Rails for building dynamic websites which looks great, it can be used for shell scripting and  gui apps.  Which package do I use for the gui apps.  Also what is the future looking like for Ruby?

For Python, from which I gather is very popular with ubuntu users I was overwhelmed with which way to go when building web apps.  I've had some experience with ASP which seemed easy just embedding the ASP in HTML.  What is the equivalent with python?

Someone put me on the right track please.[/QUOTE]

Both tools are useful and they have similarities as well as differences.  They both can pretty much be used to accomplish the same sorts of tasks, so the choice boils down more to asthetics than language features, in my opinion.

I am more familiar with Python that Ruby, so I can't offer much advice about Ruby packages.

There are about a zillion web frameworks in Python-- I recall reading that Turbogears is the name of a python framework that is supposed to be similar to Rails, but I have never used either.  CherryPy is another popular framework, but there are many others.

As for GUIs, the popular ones include Tkinter and wxPython.  Python bindings exist for lots of other popoular toolkits, including Qt  and GTK.

My advice would be to just pick one and try it out.  If you don't like it, you can try the other.

---

### Post by j-a-p on 2005-12-30
Thanks for the quick replies people.

Quoting cwaldbieser "There are about a zillion web frameworks in Python".  It looks as if I need to give one a go as you say.  I just don't like spending loads of time on something to find out I should have been using something else.  I suppose that's the nature of the beast though.

You mentioned Tkinter and wxPython for gui development, would you happen to know what the equivalent is for Ruby?

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=j-a-p]Thanks for the quick replies people.

Quoting cwaldbieser "There are about a zillion web frameworks in Python".  It looks as if I need to give one a go as you say.  I just don't like spending loads of time on something to find out I should have been using something else.  I suppose that's the nature of the beast though.

You mentioned Tkinter and wxPython for gui development, would you happen to know what the equivalent is for Ruby?[/QUOTE]

Well, the GUI toolkits are really independent of Python-- I think wxWindows has either a native C or C++ API, and Tk has its roots in the TCL scripting language.  Many times, someone will create scripting language bindings to these types of external frameworks and libraries (including GUIs, DBs, web frameworks, etc.), so I would not be surprised if Ruby had packages that you could use to use any of these tool kits as well.

I find the best place to ask Python related questions is the comp.lang.python newsgroup.  I am not sure what serves as the "backbone" of the Ruby community, but it looks like they have a mailing list on the main web site.  Possibly they have a Wiki or newsgroup.

---

### Post by thumper on 2005-12-30
Is there any reason why you don't want to learn both?

Personally I am a python (and C++) person, but I can see some cool stuff in Ruby.

---

### Post by briancurtin on 2005-12-30
[QUOTE=j-a-p]I just don't like spending loads of time on something to find out I should have been using something else.  I suppose that's the nature of the beast though.[/QUOTE]
thats good time spent though, because you learn to know why that framework isnt good for X things and why its good for Y things, even if you dont end up using it.

if you think you found what you want on the first try, dont stop there. you will find something better, or you will learn about something else, and that always helps.

---

### Post by Omnios on 2005-12-30
[How to Think Like a Computer Scientist: Learning with Python]("http://greenteapress.com/thinkpython/")

 You may find this usefull it was mentioned on G4 teck tv and the easiest newbie friendly programming book and its free.

---

### Post by j-a-p on 2005-12-31
[QUOTE=thumper]Is there any reason why you don't want to learn both?

Personally I am a python (and C++) person, but I can see some cool stuff in Ruby.[/QUOTE]

Well it's not that I dont want to learn C++, but as I said, it just got a bit heavy going for me.  I suppose ultimately I would like to the ability, but at the moment I think it's a bit out of my league!

---

### Post by j-a-p on 2005-12-31
Is there any to create the graphical interface like visual studio and then write the code behind.  It just seems tedious to have to code all the visual stuff?

---

### Post by j-a-p on 2005-12-31
[QUOTE=Omnios][How to Think Like a Computer Scientist: Learning with Python]("http://greenteapress.com/thinkpython/")

 You may find this usefull it was mentioned on G4 teck tv and the easiest newbie friendly programming book and its free.[/QUOTE]

I have seen this book and it looks superb.  I suppose I could use the C++ version too.

---

### Post by asimon on 2005-12-31
[QUOTE=j-a-p]Is there any to create the graphical interface like visual studio and then write the code behind.  It just seems tedious to have to code all the visual stuff?[/QUOTE]
If you use GTK+ then you can use Glade as UI builder, if you use Qt use it's designer. GTK+ and Qt can be used with both Ruby and Python. I am currently reading the Book "Programming Ruby - The Pragmatic Programmer's Guide" and so far I love Ruby. I like Ruby more then Python but that's a personal preference.

I you want to do web development you should take a look at Ruby on Rails, it seems to be a very good web development framework and has got a lot of praise and momentum (and of course a good share of hype) in the last couple of months.

---

### Post by j-a-p on 2005-12-31
I have decided to continue with Ruby for the time being.  I'm currently looking at ruby-GNOME2, which seems prerry straight forward so far although I would still prefer a graphical interface builder.  I looked at glade but am unsure as to whether it's got any ruby stuff.

Am I on the right track here?

---

### Post by asimon on 2005-12-31
[QUOTE=j-a-p]I looked at glade but am unsure as to whether it's got any ruby stuff.[/QUOTE]
Glade itself has no ruby support, the usual way it to save the UI description, which is an XML file (foobar.glade) and then in your app you use libglade which reads this description and builds the UI from it.
```
$ apt-cache search glade2|grep ruby
libglade2-ruby - Libglade 2 bindings for the Ruby language
```
Thus libglade bindings for ruby are there. If you install it you'll find some small examples under /usr/share/doc/libglade2-ruby/examples/ . I am sure there is also somewhere a tutorial or documentation and more examples about how to use this, but you'll have to google for it, I have no link handy.

---

