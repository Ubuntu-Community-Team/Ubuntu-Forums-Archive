---
title: "rails help please"
date: 2006-11-08
forum: Programming Talk
---

### Post by Blacktalon on 2006-11-08
Hi everyone,
I am creating an audit log for a web application at work.  And I need to be able to put the controller name in the migration table in ruby on rails, to show who did what to what.  I am not quite sure how to go about this, I currently have it like this just until I or someone else can help me figure out how to currectly do this....

t.column :Controller, :Controller => Controller.name

I highly doubt this is correct, but its just something to help me think.


Thanks,
~BT

---

### Post by skeeterbug on 2006-11-09
This is where I got started with migrations:
[http://glu.ttono.us/articles/2005/10/27/the-joy-of-migrations]("http://glu.ttono.us/articles/2005/10/27/the-joy-of-migrations")

The API docs are a good place to go too:
[http://api.rubyonrails.com/classes/ActiveRecord/Migration.html]("http://api.rubyonrails.com/classes/ActiveRecord/Migration.html")

---

