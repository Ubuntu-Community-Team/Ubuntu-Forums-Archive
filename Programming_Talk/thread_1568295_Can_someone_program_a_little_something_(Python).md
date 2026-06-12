---
title: "Can someone program a little something? (Python)"
date: 2010-09-05
forum: Programming Talk
---

### Post by James78 on 2010-09-05
**[COLOR="Red"]NOTE: Their site seems to be going up and down lately...[/COLOR]**

I tried programming this, but I kept hitting the wall. I can do lots of basic things in programming languages I don't even know, but sometimes that's not enough, because you actually have to know a language! I read a little bit of the documentation for Werkzeug (which is what this app is based on in programming), and for someone that really does know how to program Python, I don't think this would be rocket science, it shouldn't be too hard actually, it's just that I don't know how Python works, and don't have time to learn it right now... :P

The application is called [LodgeIt]("http://dev.pocoo.org/projects/lodgeit"), it's a pastebin, but it's without a delete paste feature (allow whoever pastes something to delete a paste).

Demo: [http://paste.pocoo.org/](http://paste.pocoo.org/)

It uses (only the stuff worth knowing):
Jinja2
Werkzeug
SQLAlchemy==0.6

Checkout:
```
hg clone http://dev.pocoo.org/hg/lodgeit-main
```

In lodgeit/views/show_paste.html I added:
```
    <div class="quick">
      <p><a href="/?reply_to={{ paste.identifier }}">{% trans %}reply{% endtrans %}</a> |
         <a href="/raw/{{ paste.identifier }}/">{% trans %}raw{% endtrans %}</a>
         {% if paste.user_hash == request.user_hash %}
         | <a href="/?delete={{ paste.identifier }}">delete</a>
                OR "/delete/{{ paste.identifier }}/"
         {% endif %}
      </p>
    </div>
```
And (still in lodgeit/views/show_paste.html):
```
        <li><a href="/raw/{{ paste.identifier }}/">{% trans %}download paste{% endtrans %}</a></li>
        {% if paste.user_hash == request.user_hash %}
            <li><a href="/?delete={{ paste.identifier }}">delete paste</a></li>
                     OR "/delete/{{ paste.identifier }}/"
        {% endif %}
```

And that makes it show only when the user is the user who posted the paste. When the person clicks the delete link, forward it to a new page (say delete_paste.html), using Werkzeug's URL internal URL rerouting feature, and ask the user, "Do you really want to delete this paste?", with 2 input buttons, Delete and Cancel.

(Please note, that even though the delete link appears to the user who made the paste, you should still handle the fact that anyone can go enter a URL into the location bar, for example /delete/10/, so you'd have to make sure that the paste.user_hash still equals the request.user_hash, but ya)

This software comes with a reply to paste feature, which causes some pastes to have a parent and child paste, so for example, if I deleted a parent paste of a child, the child would need to be updated to say it's a parent paste, or a child of the parent paste back up the line (the paste tree), that'd have to be handled correctly.

I really hope someone will be kind enough to do this for me! I'll take your changes and post them on their development site as a patch, and give the credits to you (unless you want to post the patch yourself). I'd really appreciate it, thanks. ;)

---

