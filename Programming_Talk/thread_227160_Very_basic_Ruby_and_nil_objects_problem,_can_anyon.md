---
title: "Very basic Ruby and nil objects problem, can anyone help?"
date: 2006-08-01
forum: Programming Talk
---

### Post by Frostmourne on 2006-08-01
I am rubbing Ruby 1.8.4 and Rails 1.1.2 on my Dapper box, and this Ruby code keeps returning "You have a nil object where you didn't expect it!" error, despite similar code working on my Windows XP box with Ruby 1.8.2 and Rails 1.1.0. I have this in my ForumsController class, so far:

```
class ForumsController < ApplicationController

  def index
    @forums = Forum.find(:all, :order => 'title ASC')
  end

  def display
    @forum = Forum.find(params[:id])
  end
end
```

If I just call the index method or do a scaffold :forum and call any of the scaffold methods, all the forums show up as expected. But if I call my display method, I get this error screen:

```
 NoMethodError in Forums#display

Showing app/views/forums/display.rhtml where line #1 raised:

You have a nil object when you didn't expect it!
The error occured while evaluating nil.title

Extracted source (around line #1): (this is my display.rhtml view)

1: <h2><%= @forum.title %></h2>
2: <p>Topics will go here.</p>
```

So what exactly is the problem? I haven't touched Ruby on Rails for a while, but on my Windows XP machine I remember this code working. Googling got me nowhere, so I would appreciate if you guys could please point me in the right direction.

---

### Post by Oldbones on 2009-12-13
Did you look at your forums controller?

---

### Post by cariboo on 2009-12-14
I hope you noticed that this thread was started in August of 2006, the op hasn't ven logged in since last January. This thread is closed.

---

