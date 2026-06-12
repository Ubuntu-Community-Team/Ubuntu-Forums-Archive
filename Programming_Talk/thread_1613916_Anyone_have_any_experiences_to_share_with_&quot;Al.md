---
title: "Anyone have any experiences to share with &quot;Alternative&quot; Python Web frameworks ?"
date: 2010-11-05
forum: Programming Talk
---

### Post by techrush on 2010-11-05
I realize the idea of a python web framework is already kind of alternative to begin with but my question is if anyone has some experience with python web frameworks other than pylons and django ? 

I looked at turbogears a couple years back and may check it out again soon. Anyone have any others to recommend ?

---

### Post by DanielWaterworth on 2010-11-05
I do. I started out in Django and found it limiting, so I branched out. I didn't like pylons' use of global variables so I steered clear and eventually made my own framework from pre-built components off the web together with some glue code. I'm planning on releasing it as open-source soon, but the components I use are:

sqlalchemy (and elixir),
jinja2 (because it's super fast, but also flexible. Dynamic inheritance is a major boon),
selector for url dispatch. It's lightweight and simple.
formencode, (actually I'm still in the process of switching to formencode, I'm using a simple form library that I wrote atm),
beaker session middleware,
python paste (exceptions/cascade/fileapp middleware, webob, reload, and coming soon paste script)
jquery (I don't like javascript, jquery makes it easier)
tinymce (not integrated yet, but it's extensive configuration options won me over)

and components I've written:

auto-csrf protection,

[LIST=1]
[*]forces post requests to be sent with the sessionid.
[*]auto annotates forms with the sessionid via javascript.
[/LIST]
glue code, ties the components together,
authentication, based on openid
tagging plugin for elixir
voting plugin for elixir, (not tied to the authentication system, you can use any elixir model as a user)
soft delete plugin for elixir,
flagging plugin for elixir,
(comments coming soon)
management script
roles system based on a simple DAG implementation.
and I'm working on auto-recommendation based on restricted boltzmann machines, (the winners of the netflix prise used this),

It forces a clear divide between business logic and presentational logic. The business logic resides within apps (like Django) and each controller returns the output of a function (thissite.render(*args, **kwargs)), which acts as a proxy to the view functions which reside in themes. This means that by changing the theme of a site you can change everything about it's appearance, (more than you can by just replacing templates), but still retain the functionality.

I'm been using it for a few months now and it's the best framework I've ever used, if there's a big demand for it becoming open source sooner rather than later I can release it this weekend.

---

### Post by juancarlospaco on 2010-11-05
web2py

---

