---
title: "Freaked out by Rails... and I haven't written any code yet"
date: 2009-01-24
forum: Programming Talk
---

### Post by teryret on 2009-01-24
Hello all.  My mother recently conned me into writing a basic forms-over-data app to help her keep track of her upstart real-estate rental management business (since I failed to find her a free one of any quality).  I'll doubtlessly opensource it eventually, but for the time being it's just a project for me and my roommate to learn rails.

I'm no stranger to programming (C# and javascript at work, Java and C++ at school), so once I get going I should be fine, but setting a workflow up is freaking me out a bit.

Most of these questions should be on the easy side but bear with me, I'm one of those programmers who likes to spend the time setting things up right before he starts building.

My questions:

1) I like Netbeans for development in Java and C++, should I use it for Rails too, or is there something better?  

2) Netbeans defaults to "Built-in JRuby 1.1.4" that seems to be configured correctly (in the Ruby Platform Manager).  When this thing goes live I don't think I want it to be running on JRuby if a "more native" implementation is available (regular ruby by chance?).  Or is there any real difference?  If it's not going to be run in JRuby when it goes live I don't think it makes sense to use that for development, right?  Assuming then that my feelings are right (I'm certainly wide open to be corrected on this of course) then I should probably set up netbeans for the "Ruby 1.8.7-p72" platform.  Trouble is the "Gem Home" and "Gem Tool" fields are red and say "RubyGems are not installed for this platform" and I can't figure out how to change that.  Do I need to change them?  I have the rubygems metapackage installed, but it's not autodetecting.  Plus the only "Gem Path" I've found that works is the jruby one.

3) What servers should I use?  I have the most experience with LAMP (now LAMR?), but in today's poking around I've found that there are a lot of other contenders for rails serving.  Does it matter which I use (given that I might wind up being the server admin when it goes live)?

4) Better to host my own SVN server/repo or to sign up at sourceforge for the initial dev period?

5) I like everything about nearlyfreespeech.net, except for their lack of rails support.  Who would you guys reccomend I look into for hosting (as nearlyfreespeech-like as possible)?

6) What else might I be missing?  What I'm really after here is to find out what you guys would consider the ideal setup for dev and release of a low volume rails app?

---

### Post by teryret on 2009-01-25
Also, I'm following the guide [http://www.netbeans.org/kb/docs/ruby/rapid-ruby-weblog.html](http://www.netbeans.org/kb/docs/ruby/rapid-ruby-weblog.html) .  I'm in the validate input section and I'm running into an issue: it doesn't doesn't work like the guide.  Here's my code:
```

 def test_invalid_with_empty_attributes
   property = Property.new
   #an empty proptery should be invalid
   assert !property.valid?
   #each required field should have an error message
   assert post.errors.invalid?(:ownerId)
   assert post.errors.invalid?(:address)
 end

```
The problem I'm getting is on the assert post.errors.invalid? lines.  It says "wrong number of arguements (0 for 1)".  If I comment out both lines the error stops.  I take this to mean there is some reason that ruby is misinterpreting what to me seems like plain as day literal arguements being passed to invalid?.  I have checked and rechecked my spelling.  Any ideas?

---

