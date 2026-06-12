---
title: "ruby rails switchtower on breezy"
date: 2005-11-29
forum: Programming Talk
---

### Post by pjstadig on 2005-11-29
I've been able to get ruby and rails installed ([http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable](http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable), etc.), but I can't get switchtower (the cool, automated deployment tool for ruby/rails) to work.

I did a > sudo gem install switchtower -y and when I follow the SwitchTower quick start ([http://manuals.rubyonrails.com/read/chapter/98#page297](http://manuals.rubyonrails.com/read/chapter/98#page297)) I get stuck when trying to run > rake remote_exec ACTION=setup to initialize my application on my web server. I fail with the error:
>  (in /home/pstadig/rails/tm5000)
loading configuration /usr/lib/ruby/gems/1.8/gems/switchtower-0.9.0/lib/switchtower/recipes/standard.rb
loading configuration ./config/deploy.rb
executing task setup
executing "mkdir -p -m 775 /var/www/tm5000/releases /var/www/tm5000/shared/system &&\n    mkdir -p -m 777 /var/www/tm5000/shared/log"
servers: ["rails.ctacorp.com"]
/usr/lib/ruby/1.8/base64.rb:59:in `decode64': undefined method `unpack' for nil:NilClass (NoMethodError)
        from /usr/lib/ruby/gems/1.8/gems/net-ssh-1.0.3/lib/net/ssh/transport/ossl/key-factory.rb:102:in `load_public_key'
        from /usr/lib/ruby/gems/1.8/gems/needle-1.2.1/lib/needle/lifecycle/proxy.rb:60:in `method_missing'
        from /usr/lib/ruby/gems/1.8/gems/net-ssh-1.0.3/lib/net/ssh/userauth/userkeys.rb:138:in `identities'
        from /usr/lib/ruby/gems/1.8/gems/net-ssh-1.0.3/lib/net/ssh/userauth/userkeys.rb:135:in `each'
        from /usr/lib/ruby/gems/1.8/gems/net-ssh-1.0.3/lib/net/ssh/userauth/userkeys.rb:135:in `identities'
        from /usr/lib/ruby/gems/1.8/gems/net-ssh-1.0.3/lib/net/ssh/userauth/methods/publickey.rb:50:in `authenticate'
        from /usr/lib/ruby/gems/1.8/gems/net-ssh-1.0.3/lib/net/ssh/userauth/driver.rb:169:in `authenticate'
        from /usr/lib/ruby/gems/1.8/gems/net-ssh-1.0.3/lib/net/ssh/userauth/driver.rb:155:in `each'
         ... 16 levels...
        from /usr/lib/ruby/gems/1.8/gems/switchtower-0.9.0/lib/switchtower/cli.rb:169:in `execute!'
        from /usr/lib/ruby/gems/1.8/gems/switchtower-0.9.0/lib/switchtower/cli.rb:7:in `execute!'
        from /usr/lib/ruby/gems/1.8/gems/switchtower-0.9.0/bin/switchtower:11
        from /usr/local/bin/switchtower:18


Does any one have any experience getting switchtower to work Breezy? I'm a ruby newbie and I'm stuck.

Thanks for any help.


Paul

---

### Post by cactus on 2005-11-29
I have never used switchtower...
but...*me reads documentation*
do you have your deployment recipe setup properly?

---

### Post by pjstadig on 2005-11-29
I believe I do have my deployment recipie setup properly. It looks to me like switchtower is erroring out when trying to do some base64 decoding of a public key identity or something. It seems like it could be an ubuntu/ruby/switchtower configuration of some kind (not necessarily my deployment profile but I could be wrong). Maybe there are some dependencies I'm missing, but I've combed through the Synaptic packages for ruby. Anyway, I think the Bas64 class it is trying to use is part of the ruby standard library?

---

### Post by pjstadig on 2005-11-29
figured it out....sorry about that.  My id_rsa.pub file just listed my key it was missing "ssh-rsa" in front of my key. The ruby net-ssl module was failing since the key was malformed.

Paul

---

### Post by cactus on 2005-11-29
well good. easy fixes are the best.
:)

---

