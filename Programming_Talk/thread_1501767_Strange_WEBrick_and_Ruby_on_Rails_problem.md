---
title: "Strange WEBrick and Ruby on Rails problem"
date: 2010-06-04
forum: Programming Talk
---

### Post by Sarki on 2010-06-04
Hello guys,


I recently bought a new laptop, and installed ROR.

The only problem is that I'm getting a really weird bug right now.

My ROR install process is quite simple, 3 lines:
sudo apt-get install ruby ruby-dev rubygems libopenssl-ruby
sudo gem install rails
sudo apt-get install libmysqlclient-dev mysql-server msql-gui-common-tools

Even though Webrick is working well, it seems that Ruby is not working properly...

As an exemple, when I create a new rails project (let's say "rails test") and then script/server right away in the newly "test" folder. When I click on "About your application’s environment" the corresponding <div> is refreshed, but there is nothing inside.
What's curious about that is the fact that webrick doesn't complains at all.

Does anyone has a clue about this ?

Thanks a lot in advance, I really need to get this fixed up.

Sarki

UPDATE

Well, it seems that first rails wasn't installed properly and I also forgot to install the mysql gem...
Anyway, problem solved.

---

