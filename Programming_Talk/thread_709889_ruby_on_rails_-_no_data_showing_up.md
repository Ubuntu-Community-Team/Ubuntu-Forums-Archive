---
title: "ruby on rails - no data showing up"
date: 2008-02-27
forum: Programming Talk
---

### Post by duuchung on 2008-02-27
I don't know whether this is the most appropriate place to ask for advice. The Ruby on Rails official site has not got a proper forum.
  
After working for several days, I finally got  Ruby on Rails  set up on my Ubuntu. I did a scaffold. 
I executed  “[http://127.0.0.1:3000/categories”](http://127.0.0.1:3000/categories”), but no data showed up with the frames.
I executed  “[http://127.0.0.1:3000/categories/show](http://127.0.0.1:3000/categories/show) ” or “[http://127.0.0.1:3000/categories/list”](http://127.0.0.1:3000/categories/list”), the error messages came up.   
/usr/lib/ruby/gems/1.8/gems/activerecord-2.0.2/lib/active_record/base.rb:1267:in `find_one'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.0.2/lib/active_record/base.rb:1250:in `find_from_ids'
/usr/lib/ruby/gems/1.8/gems/activerecord-2.0.2/lib/active_record/base.rb:504:in `find'
app/controllers/categories_controller.rb:16:in `show'
my settings:
Ruby version1.8.6 (i486-linux)
RubyGems version1.0.1
Rails version2.0.2
Active Record version2.0.2
Action Pack version2.0.2
Active Resource version2.0.2
Action Mailer version2.0.2
Active Support version2.0.2
Application root/var/www/ToDo
Environment development
Database adapter mysql

My database has been properly connected. I downloaded an API module from tmtm.org and checked the connection with simple.rb at [http://www.kitebird.com/articles/ruby-mysql.html#TOC_1](http://www.kitebird.com/articles/ruby-mysql.html#TOC_1)
by Paul DuBois.

I tried with another project. I still could not solve the above problems. I googled some time but to no avail.

---

### Post by duuchung on 2008-03-04
There is a forum for ruby on rails users at [http://www.ruby-forum.com](http://www.ruby-forum.com).
 Rails has moved on quite a bit since version 2.0.  Most of the tutorials are really out of date. I read the tutorials on the Akita on  Rails site and had my problem solved

duuchung

---

### Post by elithrar on 2008-03-04
[http://railsforum.com/](http://railsforum.com/) is also a good place to check.

---

