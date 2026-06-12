---
title: "Ruby on Rails - Trying to send mail with :sendmail"
date: 2009-11-29
forum: Programming Talk
---

### Post by thenetduck on 2009-11-29
Hi

I'm new to sending email with rails (and anything except gmail at that) and I am trying to get my rails app to send a message using ActionMailer. Here are my configurations in my enviroment.rb file 

```
  ActionMailer::Base.delivery_method = :sendmail
  ActionMailer::Base.perform_deliveries = true
  ActionMailer::Base.raise_delivery_errors = true
  ActionMailer::Base.default_charset = "utf-8"
  ActionMailer::Base.default_content_type = "text/html"
  ActionMailer::Base.sendmail_settings = {
    :location       => '/usr/sbin/sendmail',
    :arguments      => '-i -t'
  }
  
```

Does this look good? I'm really confused because it wont' seem to send an email from my machine. 
In my logs it looks like it sends everything perfectly. 

- The Net Duck

---

