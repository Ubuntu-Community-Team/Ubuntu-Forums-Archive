---
title: "RoR syntax error. Where did I go wrong?"
date: 2011-04-13
forum: Programming Talk
---

### Post by andy_blah on 2011-04-13
Hello,
Been trying to follow [this]("http://joneslee85.wordpress.com/2010/07/25/howto-recover-wordpress-posts-from-google-reader") guide with a Ruby on Rails script, did all the modifications, and finally saved the file. The only problem it retuns this:

```
RSS.rb:48: syntax error, unexpected tIDENTIFIER, expecting kDO or '{' or '('
...035/state/com.google/starred?n=12
                              ^
```

Can anyone advise me what to do?
Thank you in advance.

---

### Post by Arndt on 2011-04-13
> **andy_blah said:**
> Hello,
Been trying to follow [this]("http://joneslee85.wordpress.com/2010/07/25/howto-recover-wordpress-posts-from-google-reader") guide with a Ruby on Rails script, did all the modifications, and finally saved the file. The only problem it retuns this:

```
RSS.rb:48: syntax error, unexpected tIDENTIFIER, expecting kDO or '{' or '('
...035/state/com.google/starred?n=12
                              ^
```

Can anyone advise me what to do?
Thank you in advance.

48 lines is not so much. Can you post the whole script?

---

### Post by andy_blah on 2011-04-13
My bad, forgot to leave the content too >.<
```
#!/usr/lib/ruby/1.9.1
require 'rubygems'
require 'simple-rss'
require 'open-uri'
require 'builder'
require 'progressbar'

source = {"http://google.com/reader/atom/user/16912036744440613035/state/com.google/starred?n=12"}
content = ""

pbar = nil

feed = SimpleRSS.parse(open(source,
      :content_length_proc => lambda {|t|
        if t && 0 < t
          pbar = ProgressBar.new("Fetching Atom Feed", t)
          pbar.file_transfer_mode
        end
      },
      :progress_proc => lambda {|s|
        pbar.set s if pbar
      }))

xml = Builder::XmlMarkup.new( :target => File.open("rss.xml", "w"), :indent => 2 )
xml.instruct!
xml.rss("version" => "0.9.2") do
  xml.channel do
    xml.title feed.channel.title
    xml.link  feed.channel.link
    xml.description "I am going to turn to RSS"
    xml.lastBuildDate feed.channel.updated
    xml.docs "http://backend.userland.com/rss092"
    xml.language "en"

    feed.items.each do | item |
      xml.item do
          xml.pubDate item.published
          xml.category item.category
          xml.title item.title
          c = item.content
          c.gsub!("\n",'')
          xml.description c
          xml.link item.link
      end
    end
  end
end
```

[QUOTE=Arndt]48 lines is not so much.[/QUOTE]

What do you mean by that? ^^;

---

### Post by Arndt on 2011-04-14
> **andy_blah said:**
> My bad, forgot to leave the content too >.<


What do you mean by that? ^^;

I meant only that it is small enough so one might see the error by inspection. But I'm not even that much at home in Ruby, so I can't help you further.

---

