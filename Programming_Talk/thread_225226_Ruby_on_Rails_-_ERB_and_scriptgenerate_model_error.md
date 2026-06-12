---
title: "Ruby on Rails - ERB and script/generate model errors"
date: 2006-07-29
forum: Programming Talk
---

### Post by RoadWarriorEWR on 2006-07-29
I recently installed Ruby on Rails on Dapper and was able to run code through the ruby compiler. However, when I try to use the native ERB, I get an error that the command isn't found. Dapper seems to install eruby instead of ERB. I've even downloaded and installed ERB from the packages, but continue to get the error: bash: erb: command not found

I can run a ruby file with integrated HTML using "eruby [file].rb", but I cannot get erb to run on my end, no matter what I install. So, that's problem number 1.

Problem number 2 is when I try to create the Rails model files. I get the following error when running "ruby script/generate model work":

*************
/usr/lib/ruby/1.8/yaml.rb:133:in `load': syntax error on line 17, col 2: ` host: localhost' (ArgumentError)
from /usr/lib/ruby/1.8/yaml.rb:133:in `load'
from /usr/lib/ruby/gems/1.8/gems/rails-1.1.4/lib/initializer.rb:459:in `database_configuration'
from /usr/lib/ruby/gems/1.8/gems/rails-1.1.4/lib/initializer.rb:181:in `initialize_database'
from /usr/lib/ruby/gems/1.8/gems/rails-1.1.4/lib/initializer.rb:84:in `process'
from /usr/lib/ruby/gems/1.8/gems/rails-1.1.4/lib/initializer.rb:42:in `run'
from ./script/../config/../config/environment.rb:13
from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
from /usr/lib/ruby/gems/1.8/gems/activesupport-1.3.1/lib/active_support/dependencies.rb:147:in `require'
from /usr/lib/ruby/gems/1.8/gems/rails-1.1.4/lib/commands/generate.rb:1
from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
from /usr/lib/ruby/gems/1.8/gems/activesupport-1.3.1/lib/active_support/dependencies.rb:147:in `require'
from script/generate:3
*************

Now, looking at lines 458-460 in initializer.rb, I see the following:
def database_configuration
YAML::load(**ERB**.new(IO.read(database_configuration_ file)).result)
end

This leads me to believe that the ERB problem is rearing its ugly head again. I have searched and searched and searched, but to no avail. And, being at the beginning of my RfR experience, I'm really at a loss. Any help would be greatly appreciated, as I basically can't move any further from here.

Thank you in advance for your help.

---

### Post by RoadWarriorEWR on 2006-07-29
I'm very humbled to say that my problem was with the database.yml file. Apparently, I didn't have a space between the "password:" and my actual password. It looked like this:

development:
adapter: mysql
database: r4rmusic1_development
username: r4r
password:myDBpassword
host: localhost

When I added the space before the password, I was able to run the ruby script/generate model script without a problem. I finally got the right search terms in google and got to it. This just goes to illustrate the point that it's usually something small.

---

