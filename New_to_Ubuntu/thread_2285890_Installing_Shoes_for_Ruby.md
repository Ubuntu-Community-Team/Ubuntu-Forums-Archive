---
title: "Installing Shoes for Ruby"
date: 2015-07-08
forum: New to Ubuntu
---

### Post by ashtron on 2015-07-08
I'm trying to install [shoes]("http://www.shoesrb.com") for Ruby on Lubuntu 14.04. After running the installer from the website I get the message

```
Shoes has been copied to /home/ashton/.shoes/federales
```

When I try to run a program containing

```
require 'shoes'
```

I get

```
/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': cannot load such file -- shoes (LoadError)
    from /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
    from tomatillo.rb:1:in `<main>'
```

I'm new to Ubuntu and have no idea what I'm doing.

Help!

---

### Post by sandyd on 2015-07-08
Shoes requires that you compile the .rb file you coded in the Shoes app.
Go to the Unity Dash, and type in Shoes. Run the app that shows up and click "Open an app"

---

### Post by ashtron on 2015-07-09
Ah, well, that explains it. Thanks.

---

