---
title: "Ferret broke Rails installation?"
date: 2007-09-27
forum: Programming Talk
---

### Post by flamingsole on 2007-09-27
So, I've been working away on a freelance project that uses Ruby on Rails. I'm still very much a beginner, but for this particular project Rails is still moving faster than PHP would have. Which is wonderful.

Today, I installed ferret, and was testing out search features. Everything was working perfectly, and in my book (RailsSpace), it said that if ferret encounters errors, one should delete its index directory. I found the command: script/console >> ModelName.rebuild_index to do this, and everything worked perfectly again.

The book also said that at the end of my search, I should include the command:

rescue Ferret::QueryParser::QueryParseException.
@invalid.

I did this, and it seems to have entirely broken my Rails and/or Ruby installation. Now, when I try to log in to the server, I get the following 500 error:

We're sorry, but something went wrong.
We've been notified about this issue and we'll take a look at it shortly.

If I try to log in to the console, I get the following: 

/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- object (MissingSourceFile)
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:495:in `require'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:342:in `new_constants_in'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:495:in `require'
        from ./script/../config/../config/../app/helpers/application_helper.rb:4
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:203:in `load_without_new_constant_marking'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:203:in `load_file'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.4.2/lib/active_support/dependencies.rb:342:in `new_constants_in'
         ... 21 levels...
        from /usr/lib/ruby/1.8/irb/init.rb:250:in `load_modules'
        from /usr/lib/ruby/1.8/irb/init.rb:21:in `setup'
        from /usr/lib/ruby/1.8/irb.rb:54:in `start'
        from /usr/bin/irb:13

I've tried to uninstall rails, gems, and ruby, and then to reinstall all of them. Nothing has helped, thus far. Any ideas on what I can do to fix this? Thanks so much.

Jon

**Update:** The problem fixed itself when I recreated the Rails app, and brought the data over via copy and paste, while executing the generate commands as if everything was being done for the first time. Interesting issue.

---

