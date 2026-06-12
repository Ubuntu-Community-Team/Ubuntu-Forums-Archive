---
title: "ubuntu, ruby and log4r"
date: 2006-09-20
forum: Programming Talk
---

### Post by jansenh on 2006-09-20
Hi Forum.

Not sure where this issue belongs... but anyhow: My **Log4r** ain't working

1 . I installed ruby-1.8.5 from source in /usr/src. (based on some blog recomendation...)
2. I installed rybygems-0.8.11 in /usr/src/

Both are working - I did a 'sudo gem install log4r' and the package installed itself.

3 . But using Log4r inside my ruby scripts is **NOT working**.


When I search for the Log4r files, I find them in /usr/local/lib/ruby/gems/1.8/gems/log4r-1.0.5/

And from here I do not know how to proceed? I haven't been arond linux in years  :confused: Anyone want to help me?

/jansenh

---

### Post by DeadEyes on 2006-09-20
I may not be able to give you the best advice as I'm only getting started with Ruby myself, and using gem never seems to work for me.
First try:

$irb
irb> require 'log4r'

If it doesn't return true then Ruby isn't finding the module. This is what happened me, so I downloaded the source extracted it and ran
```

$sudo ruby install.rb
$irb
irb> require 'log4r'
=> true
irb> include Log4r
irb> mylog = Logger.new 'mylog'
irb> mylog.outputters = Outputter.stdout
irb> mylog.debug("hello world")
DEBUG mylog: hello

```

If you get that far your laughing.

---

### Post by Jessehk on 2006-09-20
When you use a gem installed by rubygems in a script, you need to 

```

require "rubygems"

```

before you *require* the gem you are using.

---

### Post by DeadEyes on 2006-09-21
Thanks for that info Jessehk, it made me think and after a quick search I found [this]("http://docs.rubygems.org/read/chapter/3#page70") from the ReubyGems manual which shows that method plus better alternative methods.

---

