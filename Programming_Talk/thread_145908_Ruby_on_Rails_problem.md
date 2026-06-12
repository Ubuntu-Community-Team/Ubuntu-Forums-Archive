---
title: "Ruby on Rails problem"
date: 2006-03-17
forum: Programming Talk
---

### Post by robtotheb on 2006-03-17
Ive been following the Agile Web Development book (teaches you ruby on rails) and installed ruby and ruby on rails with no errors but when I try to run the 1st action - "Hello from Ruby"  the page just outputs nothing.  I have triple checked I didn't make any errors.

Any one have dapper and ruby on rails working?

```
127.0.0.1 - - [17/Mar/2006:12:35:14 GMT] "GET /say/hello HTTP/1.1" 200 0
- -> /say/hello
[2006-03-17 12:35:14] ERROR MissingSourceFile: no such file to load -- irb
        /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__'
        /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:214:in `require'
        /usr/lib/ruby/gems/1.8/gems/rails-1.0.0/lib/breakpoint.rb:18
        /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:207:in `load'
        /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:39:in `require_or_load'
        /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:22:in `depend_on'
        /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:178:in `require_dependency'
        /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:194:in `const_missing'
        /usr/lib/ruby/gems/1.8/gems/rails-1.0.0/lib/dispatcher.rb:77:in `reset_after_dispatch'
        /usr/lib/ruby/gems/1.8/gems/rails-1.0.0/lib/dispatcher.rb:46:in `dispatch'
        /usr/lib/ruby/gems/1.8/gems/rails-1.0.0/lib/webrick_server.rb:117:in `handle_dispatch'
        /usr/lib/ruby/gems/1.8/gems/rails-1.0.0/lib/webrick_server.rb:83:in `service'
        /usr/lib/ruby/1.8/webrick/httpserver.rb:104:in `service'
        /usr/lib/ruby/1.8/webrick/httpserver.rb:65:in `run'
        /usr/lib/ruby/1.8/webrick/server.rb:173:in `start_thread'
        /usr/lib/ruby/1.8/webrick/server.rb:162:in `start_thread'
        /usr/lib/ruby/1.8/webrick/server.rb:95:in `start'
        /usr/lib/ruby/1.8/webrick/server.rb:92:in `start'
        /usr/lib/ruby/1.8/webrick/server.rb:23:in `start'
        /usr/lib/ruby/1.8/webrick/server.rb:82:in `start'
        /usr/lib/ruby/gems/1.8/gems/rails-1.0.0/lib/webrick_server.rb:69:in `dispatch'
        /usr/lib/ruby/gems/1.8/gems/rails-1.0.0/lib/commands/servers/webrick.rb:59
        /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:214:in `require'
        /usr/lib/ruby/gems/1.8/gems/rails-1.0.0/lib/commands/server.rb:28
        /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:214:in `require'
        script/server:3

```

---

### Post by jcs296 on 2006-03-19
Did you install the 'irb' package? (`sudo apt-get install irb`) The Ubuntu (and Debian) repository has the Ruby package split up into multiple packages. You'll have to install rake, rdoc, and irb to get the full functionality.

For future reference, notice that the first line of the error says 'no file to load -- irb'. That means it can't find the irb library, which is a clue as to the library you'll need to install. The names don't always match, but it's a start.

---

### Post by robtotheb on 2006-03-20
Thanks jcs296 - all works great now.  \\:D/

---

### Post by jcs296 on 2006-03-21
Happy to help...enjoy Rails!

---

### Post by achron on 2006-11-21
I'm working through a RoR install/setup...  all seemed to be going well, Ruby, Rails, Eclipse, RadRails, MySQL server, SQL Users, SQL Database, edited  database.yml...  until my first RAKE DB:MIGRATE attempt.

I've been down this road many a time in that *other* operating $ystem, but there's something not quite right in the MySQL setup I guess.

I get a:

rake aborted!
No such file or directory - /tmp/mysql.sock

Any hints?

Thanks in advance!!!

---

### Post by achron on 2006-11-21
A little sleep goes a long way...  my MySQL install and the Rails install have different notions of where the mysql.sock is located... Rails/rake wants /tmp/mysql.sock, whereas MySQL Administrator reports a totally different path under Server Information...  so if I true these two up, it should work.

---

### Post by emperon on 2006-11-22
adapter: mysql
  database: almatis_development
  username: root
  encoding: utf8
  password:
  host: localhost
  socket: '/var/run/mysqld/mysqld.sock'


my database.yml file , just configure the last line . it should work

---

### Post by hedgie on 2007-01-21
I just installed  RoR on Drake

so I am a newbie, but I have no problem so far.

This is my first script:

------------------------------------

puts 1 +2

puts "hello world"
------------------------------

 I do:   ruby r1.rb

and get 
pandp@mousie:~/WORK/ruby$ ruby r1.rb
3
hello world

I followed this tut to install:
[http://ariejan.net/2006/12/03/installing-rails-on-ubuntu-dapper-edgy/](http://ariejan.net/2006/12/03/installing-rails-on-ubuntu-dapper-edgy/)
  

  hedgie

---

### Post by ronb on 2007-02-25
I'm running Dapper, and I installed Ruby, RubyGems and Rails using the following Ubuntu tutorial: [https://help.ubuntu.com/community/RubyOnRails]("https://help.ubuntu.com/community/RubyOnRails")

Everything worked except getting to a database. I have MySQL, so I downloaded the following package: **libdbd-mysql-ruby1.8**

Now everything works. 

I've just started reading *Ruby For Rails* by David A. Black and *Ruby on Rails: Up and Running* by Bruce A. Tate and Curt Hibbs. I think that both books are going to be very good.

---

### Post by foxiness on 2007-03-26
> **ronb said:**
> 
I've just started reading *Ruby For Rails* by David A. Black and *Ruby on Rails: Up and Running* by Bruce A. Tate and Curt Hibbs. I think that both books are going to be very good.

i see you start reading before 4 week and am start reading about ruby and rails from 2 week or so,i start by agile web development with rails,but its for one who know ruby will,,

can you or other here recommend a book to one need to come a web developer ?

---

### Post by ronb on 2007-03-29
> **foxiness said:**
> can you or other here recommend a book to one need to come a web developer ?

[LIST]
[*]**HTML **- *Sams Teach Yourself Web Publishing with HTML and CSS in One Hour a Day (5th Edition)* by Laura Lemay. I have not read this specific book, but I did read one of hers about 7 years ago that gave me a good start on the basics of building a web page.
[*]**CSS **- *More Eric Meyer on CSS* by Eric Meyer. This gave me a good start on CSS. 
Also, *CSS Mastery: Advanced Web Standards Solutions*  by Andy Budd, Simon Collison, and Cameron Moll. This goes beyond the basics and is easy to read.
[*]**JavaScript **- *DOM Scripting: Web Design with JavaScript and the Document Object Model*  by Jeremy Keith. DOM scripting seems like a better way to use JavaScript. This was good reading also.
[/LIST]

---

