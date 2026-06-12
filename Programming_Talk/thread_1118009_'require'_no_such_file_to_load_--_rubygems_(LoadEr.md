---
title: "'require': no such file to load -- rubygems (LoadError)"
date: 2009-04-06
forum: Programming Talk
---

### Post by cdwillis on 2009-04-06
I'm trying to learn web scraping with ruby and I've installed both the rubygems and rubygems1.8 packages but when I try to run my code I get this error:
> 
TweetScrape.rb:3:in `require': no such file to load -- rubygems (LoadError)
        from TweetScrape.rb:3


here's the code:
```

#!/bin/user/env ruby

require 'rubygems'
require 'scrubyt'
 
# Simple exmaple for scraping basic
# information from a public Twitter
# account.
 
# Scrubyt.logger = Scrubyt::Logger.new
 
twitter_data = Scrubyt::Extractor.define do
  fetch 'http://www.twitter.com/cashdollaz'
 
  profile_info '//ul[@class="about vcard entry-author"]' do
    full_name "//li//span[@class='fn']"
    location "//li//span[@class='adr']"
    website "//li//a[@class='url']/@href"
    bio "//li//span[@class='bio']"
  end
end
 
puts twitter_data.to_xml

```

I've even restarted since I installed those packages. Any help is appreciated.

---

### Post by cdwillis on 2009-04-06
I forgot to add I'm using the 9.04 Jaunty Jackalope beta (using Geany if that helps too):popcorn:

---

### Post by Tibuda on 2009-04-07
I don't know about Jaunty, but I had problems with the RubyGems version in the Intrepid repositories, so I [installed the last version from the source code]("http://rubygems.org/read/chapter/3").

---

### Post by cdwillis on 2009-04-07
Thanks for the idea Daniel. I installed ruby gems from the source but it still wouldn't work. I tried running Geany as root and it can load gems that way so it must be some sort of permission problem. :mad:

---

