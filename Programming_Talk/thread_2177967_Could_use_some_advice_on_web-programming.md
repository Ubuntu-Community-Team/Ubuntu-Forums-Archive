---
title: "Could use some advice on web-programming"
date: 2013-10-01
forum: Programming Talk
---

### Post by Zirts on 2013-10-01
[COLOR=#282828][FONT=helvetica]Hi![/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]So I am a new CS student going on the first year. We have the usual programming lessons and also a web-programming lesson. In the last one we do it with PHP in XAMPP.[/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]Now I personally really love the feel of languages like Python, C++, Java and such. But PHP...  it just does not click with me at all.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]So I found something called Ruby. I went to [http://www.codecademy.com/tracks/ruby](http://www.codecademy.com/tracks/ruby) and started learning it right away to see how it is and I have to say the language felt amazing, so many possiblities and such a nice syntax. But then when I had learned it for some time, I ofcourse wanted to utilize thoes skills and use them in webpages (we are allowed to use whatever language we want in the course, you just have to get the job done like everyone else does).[/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]Now this is where I was intrduced to Ruby on Rails and this is also where I started to not like it anymore really. The language is great but so much hassle to really use it.. [/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]So my question or so here is, can anyone give some guidance for me a bit, is it wort even taking the road?[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]I now got my RubyStack installed on my PC so I have the environment set, but the way Ruby deals with a simple webpage is very confusing to me currently and I am failing to find a decent guide on how-to use it also.[/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]And also, if I am to go the Ruby way, can I use PHP and Ruby together on a web-page? We have a group assignement coing also soon and I would need both of thoes languages to work there.[/FONT][/COLOR]

---

### Post by trent.josephsen on 2013-10-01
Rails isn't for everyone. (I don't know Ruby, but I can say that with confidence nevertheless because it's true of basically everything.) If you don't like Rails, nobody's forcing you to use it. If I were in your position, I'd consider looking at other web frameworks -- actually, if you're new to web development, I'd encourage you to avoid frameworks entirely for a while. There's definitely a risk of skipping the "boring stuff" and suddenly finding yourself in over your head, especially if you let a framework do the menial tasks for you. (Menial tasks are only menial when you've done them at least once already, and have little to gain from doing them again, which is probably not true for most newbies.)

You might want to try doing Web development in another language, like Perl (which is probably what I'd use) or Python. Since you know Ruby already, it shouldn't be too much work to pick one of those up, if you want to. Or you could just use Ruby de-Railed -- the feasibility of that depends on how sophisticated your project needs to be, but it ought to be easy to do a lot of stuff with a mini-framework of a few hundred lines or so for doing stuff like 'puts "Content-type: text/html"', etc. in response to every request. Of course, that depends on your understanding how to do that. (Often the hardest part of creating a web application, at least in my experience, is getting the Web server to behave.)

You may find that Web development isn't your cup of tea. That happened to me in high school, and I became a EE instead (though I still dabble). Fortunately, programmers have a lot of horizontal mobility, so just slog through the class and then order an Arduino or something to get a different taste of the field.

I guess I'm not completely sure what specifically you're wondering about being "worth it". Rails, Ruby, Web development, or programming in general?

---

### Post by ofnuts on 2013-10-02
> **Zirts said:**
> [COLOR=#282828][FONT=helvetica]Hi![/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]So I am a new CS student going on the first year. We have the usual programming lessons and also a web-programming lesson. In the last one we do it with PHP in XAMPP.[/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]Now I personally really love the feel of languages like Python, C++, Java and such. But PHP...  it just does not click with me at all.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]So I found something called Ruby. I went to [http://www.codecademy.com/tracks/ruby](http://www.codecademy.com/tracks/ruby) and started learning it right away to see how it is and I have to say the language felt amazing, so many possiblities and such a nice syntax. But then when I had learned it for some time, I ofcourse wanted to utilize thoes skills and use them in webpages (we are allowed to use whatever language we want in the course, you just have to get the job done like everyone else does).[/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]Now this is where I was intrduced to Ruby on Rails and this is also where I started to not like it anymore really. The language is great but so much hassle to really use it.. [/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]So my question or so here is, can anyone give some guidance for me a bit, is it wort even taking the road?[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]I now got my RubyStack installed on my PC so I have the environment set, but the way Ruby deals with a simple webpage is very confusing to me currently and I am failing to find a decent guide on how-to use it also.[/FONT][/COLOR]

[COLOR=#282828][FONT=helvetica]And also, if I am to go the Ruby way, can I use PHP and Ruby together on a web-page? We have a group assignement coing also soon and I would need both of thoes languages to work there.[/FONT][/COLOR]

IMHO, even if you don't like PHP, stick with it, or find another class/field. Everyone around you is going to talk PHP, the teacher's examples are likely going to e PHP (and you'll have to be familiar enough to understand them), not even speaking of working with others (which means that you shoul dbe able to read their code, and they should be able to read yours...). This shouldn't prevent you from working on your own extra-curricular projects in Java or Ruby.

And it's a good start, in any IT career you occasionally have to work with things you totally despise(*).


(*) I recently inherited the maintenance of a totally gross piece of Excel/VisualBasic that interfaces with HP's Quality Center. Still undecided on which one is the worst.

---

### Post by CCgirl6690 on 2013-10-04
how long did it take for you to learn PHP?  i want to start learning too

---

### Post by SeijiSensei on 2013-10-04
It took me a couple of weeks to be able to build a web site with PHP that included a SQL database backend (PostgreSQL in my case).  I had designed a site with static pages for my college reunion class, but wanted to add a classmate directory.  That required learning about forms-processing and database transactions.  I hadn't programmed since college, some 25 years before, when I learned things like FORTRAN.  I had some limited experience with databases from building applications in MS Access, but that was it.

Based on my experience I suggest identifying a project that interests you and start with that.  Learning a language in the abstract is, at least for me, a fairly unhelpful approach.  After you get past the basics, I'd try designing a site that uses "[sessions]("http://php.net/manual/en/features.sessions.php")" then see if you can build a site that includes user logins.

---

### Post by Kevin_Arnold on 2013-10-04
What is it you don't like about PHP? I'd look in to using a template engine (twig, smarty) or even a full PHP framework (Symfony, CakePHP).

As you noticed with Rails, most of the frameworks have a lot of rules about how you have to do stuff. Once you know it, it makes creating quick CRUD pages really fast but until then it'll be tough. The simplest thing would be to just use plain old PHP and twig.

I'm a big fan of C# and MVC4 as well but I assume you're looking for stuff to easily setup and run on linux.

Edit: Also, make sure to use PHP's OOP features to their fullest. It really makes PHP much more bearable.

---

### Post by 1clue on 2013-10-04
Ruby/Rails is being actively used.  This is a language (ruby) and a web framework (rails) that is getting better every year, it's definitely in its earlier stage of development and worth learning.

Look up a guy named Neal Ford.  He has tips about ruby/rails and is all about common sense.  At one point he had quite a library of examples for ruby/rails, he probably still does.

I'm not really into ruby/rails but I've gone to the "No fluff just stuff" events for a few years.  I'm using groovy/grails and other languages that leverage the Java virtual machine, but ruby/rails is talked about by several of the guys there.  Neal Ford is brilliant not only on programming but also on productivity in general.

---

### Post by llanitedave on 2013-10-05
> **ofnuts said:**
> IMHO, even if you don't like PHP, stick with it, or find another class/field. Everyone around you is going to talk PHP, the teacher's examples are likely going to e PHP (and you'll have to be familiar enough to understand them), not even speaking of working with others (which means that you shoul dbe able to read their code, and they should be able to read yours...). This shouldn't prevent you from working on your own extra-curricular projects in Java or Ruby.

And it's a good start, in any IT career you occasionally have to work with things you totally despise(*).


(*) I recently inherited the maintenance of a totally gross piece of Excel/VisualBasic that interfaces with HP's Quality Center. Still undecided on which one is the worst.


I never liked PHP either:  in fact, it was learning PHP that motivated me to try Python instead, and I haven't looked back.

Still, ofnuts offers wise advice.  If the class is concentrating on PHP, and that is what the instructor is most comfortable with, it will do you no harm to learn it.  And knowing it will make you appreciate elegant languages like Python and Ruby that much more.

---

### Post by 1clue on 2013-10-05
+1 on ofnnuts' comment.  PHP is pretty much the industry standard for web programming.  I never learned it, but I started programming back in the 80s.  I've been tempted to pick it up, but never found the time.

Anyway, for somebody who's just starting out PHP is a must-have.  I doubt you'll make a lot of money with it though because EVERYONE will know it, and somebody will almost always be hungrier than you are.  It will probably be a must on your resume, but it won't get you a great job all by itself.

Your ruby/rails idea is a good one, it's a solid language with enough support to keep it under development, and it's a young language yet that only started to emerge from obscurity a few years ago.  As such you'll probably be best to get on the wagon early.

---

### Post by ofnuts on 2013-10-05
> **1clue said:**
> PHP is pretty much the industry standard for web programming.

**[FONT=fixedsys]s/the/one of the/[/FONT]** 

Let's not forget Java :)

---

### Post by slickymaster on 2013-10-05
> **ofnuts said:**
> **[FONT=fixedsys]s/the/one of the/[/FONT]** 

Let's not forget Java :)
^^^^ Exactly.
Twitter for example was built using Rails/Ruby but once it became unscalable, they migrated to the JVM.

---

### Post by 1clue on 2013-10-05
There's a lot of Java hate going around, mostly on Linux forums AFAICT.

For the past 15 years or so I've been working almost exclusively on the Java virtual machine.  I'm doing groovy/grails right now, which has a lot in common with ruby/rails from what I understand.

<soapbox type="java">
There are a lot of languages that compile to Java byte code.  Over 200 last I looked it up, but that was a few years ago.

Java is on more CPUs than Windows is.  It's on everything from supercomputers to embedded processors which have no UI.

[LIST=1]
[*]If you use Oracle financial software at work, you're using Java.
[*]If you use Oracle database, you're probably using Java.
[*]If you watch BluRay, then you use Java.
[*]If you have a smart phone or tablet, you're probably using Java.
[/LIST]

IMO Java inside a web browser is not a great idea, but on the server it's excellent.  The server VM compiles into very fast code (comparable to bare-metal compiled code speeds) on startup, and it stays running for days or months or however long, so the initial startup cost is relatively small.  It is somewhat isolated from the hardware so it's a bit safer in that respect.

There ARE security issues with it, especially lately.  Nothing's perfect.

IMO the free version of Java is not nearly as reliable nor as good as the official version.
</soapbox>

---

### Post by Zirts on 2013-11-16
I went with Rails. Have been learning it till now almoust every day and well... There are a lot of holes I need to fill in my knowlage of web development all the time but other than that I kinda love the language and framework allready.
Thanks for all the replies :)

---

