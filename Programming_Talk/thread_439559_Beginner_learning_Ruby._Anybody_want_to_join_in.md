---
title: "Beginner learning Ruby. Anybody want to join in?"
date: 2007-05-10
forum: Programming Talk
---

### Post by katabatic on 2007-05-10
I'm a beginner programmer and learning Ruby. Anybody here doing the same and want to join and learn together? Bored here. :popcorn:

---

### Post by slavik on 2007-05-10
well, I am very comfortable with Perl ... but don't mind learning Ruby :)

---

### Post by katabatic on 2007-05-11
:guitar: .

---

### Post by n0dl on 2007-05-11
I have the pickaxe right beside me, and it seems to be the next on my "to read" list. Count me in.

---

### Post by tc101 on 2007-05-11
I am learning Ruby.  For me learning the language is very easy.  I have been programming most of my life and it is similar enough to other things I have done that it is not much trouble.

My problems are getting the environment set up.  

I love actually writing code.  I don't like setting up computers.  I never could get it to work in Eclipse so now am just writing code in gedit and running it from the command line.

I have not installed rails yet.  My mysql install has problems.  I find all this a pain, but love coding.

What is your background in programming?  Are you having any problems?  I will answer any questions I can.

---

### Post by katabatic on 2007-05-11
I am beginner in programming.

---

### Post by nicholas22 on 2007-05-11
...or you could try Tomcat/JSP programming with Netbeans which is kewl and runs out of the box... :KS

---

### Post by katabatic on 2007-05-12
.

---

### Post by tomt on 2007-05-14
Hey. I was using Ruby on Rails (just starting out) on my old pc. Trying to get started using it now I've switched to Ubuntu. Still have no idea how to install RoR on Linux.

---

### Post by elst on 2007-05-14
tomt:

I've only dabbled, but the best method seems to be to install the basic ruby and ruby-gems packages supplied by the distribution, and then use the Ruby Gems package manager to fetch Rails etc. That way you can keep up with the new releases as they come out by upgrading with Ruby Gems.

---

### Post by daz4126 on 2007-05-14
I'm learning Ruby so that I can program in Rails. For those that asked, here is how to set it up (you might need to change the file name for ruby gems to the latest version):
```

sudo aptitude install ruby rdoc irb ri
cd
wget [http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz](http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz)
tar -zvfx rubygems-0.9.0.tgz
cd rubygems-0.9.0/
sudo ruby setup.rb
sudo gem install rails
```

For those of you looking for an editor, see my other post (Great Rails Editor for Gnome) - Scribes fits the bill if it is set up properly.

I love what I've done so far in Ruby - it such an elegant language.

Maybe for us all to learn, we should set each challenges, like the weekly programming challenge that used to grace this forum. Nothing too hard, though, as we are all learning - just something to provide motivation.

DAZ

---

### Post by daz4126 on 2007-05-14
Here's a guide a wrote to starting your own Rails blog - just something basic to get your first rails app up and running:

**Ruby on Rails Blog Project**
Get software ready
Fire up a text editor, terminal, folder and firefox

go to terminal, navigate to the folder where you want to keep all your rails projects, then type:
```
$ rails blog
```

This will create the Rails directory structure, now type:
```
$ cd blog
```

to change to the blog directory.
Now type
```
$ ruby script/server
```

This will launch the built-in mongrel server. Go into firefox and visit [http://localhost:3000](http://localhost:3000)
You should get the Ruby on Rails congratulations page to say that you are on board and riding the rails!

**Create Databases**

To set up a mysql password for the first time, log in
```
mysql -u root -p
```
just press enter (there is no password set initially)
Then type:
```
use mysql;
update user set password=PASSWORD("p@$$word") where User='root';
flush privileges;
quit;
```

Now go back to the terminal and launch mysql as the root user
```
$ mysql -u root -p
$ [enter your password]
```

Create the development database:
```
mysql> create database blog_development;
mysql> create database blog_test;
mysql> create database blog_production;
```

Grant priveliges on these database to your normal user: 
```
mysql> grant all privileges on blog_development.* to 'username'@'localhost' identified by 'p@$$word';
mysql> grant all privileges on blog_test.* to 'username'@'localhost' identified by 'p@$$word';
mysql> grant all privileges on blog_production.* to 'username'@'localhost' identified by 'p@$$word';
```

open the database.yml file with a text editor (it's in >blog>config>database.yml) and fill in each database connection info as:
```
  adapter: mysql
  database: blog_development
  username: username
  password: p@$$word
  host: localhost

```
save the file and close it

Go into the terminal and navigate to the blog folder and type:

```
blog$ rake db:migrate
```

This will test to see if rails can connect to the database

**NOTE - you might get an error here about require_gem being obsolete. To remedy this, open the file boot.rb (in the same config folder as database.yml) and change the reference to require_gem to just 'gem'**

**Create Posts Model**
Go back into the terminal and type:
```
blog $ ruby script /generate model Post
```

This will create a model for the blog's posts.

Now go into the migration file, 001_create_posts.rb (path: blog>db>migrate>001_create_posts.rb) and create the relevant columns for the database:
```

class CreatePosts < ActiveRecord::Migration

  def self.up
    create_table :posts do |t|
        t.column :title, :string
        t.column :body, :text
        t.colum :posted_on, :datetime
    end
  end

  def self.down
    drop_table :posts
  end
end
```


Go into the terminal and navigate to the blog folder and type:

```
blog$ rake db:migrate
```

This will add the table 'posts' and three columns to the database.

**Build some Scaffolding and then enter some data:**
open the file post_controller.rb file (path: blog>app>controllers>post_controller.rb) and change it to:
```
class PostController < ApplicationController
    scaffold :post
end
```

Now go to [http://localhost:3000/post](http://localhost:3000/post) in your web browser.
You should now see an interface that will allow you to add new posts. Add some test posts and enjoy....


DAZ

---

### Post by elst on 2007-05-14
I'm not sure whether it was there in previous versions, but Feisty has a package for Ruby Gems 0.9.0 ("rubygems", no hyphen), so you can now install it along with the main Ruby packages.

The bit that I'm finding the hardest is wiring up Rails applications to work with standard Web servers - Lighttpd with FastCGI at present, but I tried Apache and FastCGI a while ago (bad idea).

---

### Post by tomt on 2007-05-16
Hey the post with the blog code was pretty exciting. 

I think when the work week from hell ends I'm going to focus on getting ruby working and try that out. I have a naffy domain name im doing nothing with after all...

The post did make me realise that I have no idea how to get SQL going in ubuntu (does open office have something) I also am not clear whether the command line instructions will be the same as they were when I was using windows.

As you can guess I'm not all that tech savvy...yet.

---

### Post by FuriousLettuce on 2007-05-16
I have to check out Rails, the structure and framework is something I've never really seen before.

---

### Post by daz4126 on 2007-05-17
tomt,

Here is the code to install mysql on Ubuntu:

Use Synaptic to install the following packages:
[LIST]
[*]mysql-server
[*]mysql-client
[*]libmysqlclient
[/LIST]

Then type the following into a terminal:

```
sudo apt-get install phpmyadmin apache2 libapache2-mod-php5
```

The terminal commands  in Ubuntu are generally the same as in Windows.

Hope that helps,

DAZ

---

### Post by daz4126 on 2007-05-17
Here is a challenge for people trying to learn Ruby:

Challenge 1 (Easy)

Write a program that asks for your name, then gives you a personalised greeting.

Extend this by having the greeting based on the current time.

Challenge 2 (harder):

Write a short program that plays higher or lower - The computer 'thinks' of a number between 1 and 100 and the player tries to guess. The computer gives feedback of 'higher' or 'lower' until the player guesses correctly.

Extend this by reversing the roles - the player thinks of a number and the computer tries to guess with feedback of higher or lower from the player.

Post any entries or questions here.

DAZ

---

### Post by FuriousLettuce on 2007-05-17
I had a quick try at this, not sure if it's is any good - there may be far easier ways to do a lot of these things in ruby, I've just applied general logic to it and got by on that. The only ruby-specific method there is .chop, so if anybody can see anyway to clean up the code then please feel free to tell me!

```
#!/usr/bin/env ruby

def get_input(msg)
	#returns an integer from user input
	printf msg
	return gets.to_i
end

def compare(unum, value)
	#compares the values passed - returns 1 if equal, otherwise 0
	if unum == value
		puts "Well done! You guessed correctly!"
		return 1
	elsif unum > value
		printf "Lower; "
		return 0
	elsif unum < value
		printf "Higher; "
		return 0
	end
end

def comp_choose()
	#called when user wants the computer to choose the number to guess
	num = 100*rand
	num = num.to_i

	puts "I have picked a number between 1 and 100."

	begin
		begin
	                unum = get_input("Please enter an integer betwen 1 and 100: ")
	        end until (unum > 0 && unum < 101)
		#qflag is 1 only when the guessed value and random value are equal
	        qflag = compare(unum, num)
	end until qflag == 1
end

def player_choose()
	#called when the user wants the computer to guess the number
	begin
		unum = get_input("Please enter an integer between 1 and 100: ")
	end until (unum > 0 && unum < 101)

	#lower and upper limits. third value is the calculated value if correct
	limits = [1, 100, 0]

	begin
		limits = find_num(limits)
		#if (lower_limit - upper_limit) == 1 then they are cheating
		if (limits[0] - limits[1]).abs == 1
			cflag = 1
			break
		#if there is only one integer between the limits, it must be the answer
		elsif (limits[0] - limits[1]).abs == 2
			limits[2] = limits[0] + 1
			break
		end
	end until limits[2] != 0

	if cflag == 1
		puts "You were cheating - there are no integers between #{limits[0]} and #{limits[1]}!"
	else
		puts "I found your number - #{limits[2]}!"
	end
end

def find_num(limits)
	begin
		cnum = rand(limits[1] -1)
	end until cnum > limits[0]			

	puts "I have thought of a number: #{cnum}"
			
	begin
		printf "Should I go (h)igher or (l)ower, or am I (c)orrect? "
		ans = gets.chop
	end until (ans == "h" || ans == "l" || ans == "c")

	if ans == "h"
		limits[0] = cnum
		return limits
	elsif ans == "l"
		limits[1] = cnum
		return limits
	else
		limits[2] = cnum
		return limits
	end
end

def main
	puts "Who would you like to pick the number"
	printf "\t1) The Computer\n\t2) The User\n"

	begin
		choice = get_input("Please enter 1 or 2: ")
	end until (choice == 1 || choice == 2)

	if choice == 1
		comp_choose
	else
		player_choose
	end
end

main
```

---

### Post by ButteBlues on 2007-05-19
> **daz4126 said:**
> Here is a challenge for people trying to learn Ruby:

Challenge 1 (Easy)

Write a program that asks for your name, then gives you a personalised greeting.

Extend this by having the greeting based on the current time.

I opened the QuickRef once or twice, but here it is:

```
class GrabInfo
  def time_stuff
    t = Time.now
    @time_to_print = t.strftime("%I:%M%p on %A %B %d, %Y")
    if t.strftime("%p") == "PM"
      if t.strftime("%I").to_i <=> 1..5
        @greeting = "Good afternoon"
      elsif t.strftime("%I").to_i <=> 6..11
        @greeting = "Good evening"
      elsif t.strftime("%I").to_i <=> 12
        @greeting = "Good afternoon"
      end
    elsif t.strftime("%p") == "AM"
      if t.strftime("%I").to_i <=> 1...4
        @greeting = "You're up late"
      elsif t.strftime("%I").to_i <=> 1...11
        @greeting = "Good morning"
      elsif t.strftime("%I").to_i <=> 12
        @greeting = "You're up late"
      end
    end
  end

  def name_stuff
    puts( "What is your name?" )
    @name = gets.strip
  end

  def print_it
    printed = puts("#{@greeting}, #{@name}! It is now #{@time_to_print}.")
  end
end

gi = GrabInfo.new
gi.time_stuff
gi.name_stuff
gi.print_it
```

Of course, you can de-Object Orient it, which removes a lot of fluff.

if you want a quick + dirty, so to speak:

```

name = gets.strip
puts("Hello, #{name}, it is now #{Time.now.strftime("%I:%M%p on %A %B %d, %Y")}.")

```

But, that's pretty messy.

---

### Post by daz4126 on 2007-05-20
Or even just one line:

puts("Hello, #{gets.strip}, it is now #{Time.now.strftime("%I:%M%p on %A %B %d, %Y")}.")


DAZ

---

### Post by coder_ on 2007-05-20
I'd suggest the [Programming Ruby]("http://pragmaticprogrammer.com/titles/ruby/index.html") book.  It's fantastic.  Also, Pragmatic Programmer's Rails book is good if you are looking to go onto Rails.

---

### Post by hasimir44 on 2007-05-26
I've been dabbling in ruby and rails for the last couple of weeks.  Ruby is so simple and so seemingly complex at first - all at the same time.. 

I've run into a probem with the environment though.  I can't get rails to connect to mysql if I use a password. If I remove the password in mysql - rails connects, add a password to the account and to the database.yml file - rails won't connect. For obvious reasons, I want to use a password.. 

I found some other posters who said that mysql had changed their password mechanism, but that was supposedly in mysql4 and I'm using mysql5 with rails 1.8 (supposedly should use the same mechanism?).  

So.. another post said to install mysql through gem - that errored out: 

```
> sudo gem install --include-dependencies mysql

Need to update 9 gems from http://gems.rubyforge.org
.........
complete
Select which gem to install for your platform (i486-linux)
 1. mysql 2.7.3 (mswin32)
 2. mysql 2.7.1 (mswin32)
 3. mysql 2.7 (ruby)
 4. mysql 2.6 (ruby)
 5. mysql 2.5.1 (ruby)
 6. Cancel installation
> 3
Building native extensions.  This could take a while...
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:1

ERROR:  While executing gem ... (RuntimeError)
    ERROR: Failed to build gem native extension.
Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/mysql-2.7 for inspection.


Results logged to /usr/lib/ruby/gems/1.8/gems/mysql-2.7/gem_make.out
```


The gem_make.out file is empty, the errors above make no sense to me, and I can't turn up anything useful in google... 

Anybody else have this problem?

I'm just a newbie to ruby, but IMO there needs to be an easy way to setup the environment if rails is going to seriously compete with other frameworks. I'm not giving up though...

---

### Post by hasimir44 on 2007-05-26
Ah.... found the answer. I needed to install a few more mysql drivers.. 

```
sudo apt-get install libdbd-mysql-ruby libdbd-mysql-ruby1.8 libdbd-mysql libdbd-mysql
```


Still not sure why gem won't install mysql, but whatver. Now I can connect to my databse with a password. I'm happy.:D

---

### Post by katabatic on 2007-05-30
Ah, hello, people. I have noticed more posts here. I'm still reading tutorials.

---

### Post by frolle on 2007-06-12
It all looks really good. I have been thinking about trying to learn Ruby, it seems quite "easy", so to speak..

---

