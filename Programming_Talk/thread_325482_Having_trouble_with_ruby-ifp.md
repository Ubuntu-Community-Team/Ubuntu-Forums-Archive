---
title: "Having trouble with ruby-ifp"
date: 2006-12-25
forum: Programming Talk
---

### Post by Third Thoughts on 2006-12-25
Hey all, I'm trying to develop a little ruby app to manage my iRiver music device. I found the ruby library ruby-ifp, which allows me to utilize the libifp driver. However, I'm having some trouble getting it working. The first problem I ran into was that the script that was generating the makefile didn't acknowledge that I had the dependencies installed. Here's that script
```

require 'mkmf2'

PACKAGE_NAME = "ifp"

req_deps = ["usb", "ruby", "ifp" ]
req_deps.each do |dep|

    if !have_library(dep) or !have_header(dep + ".h")
        printf "!!!Error.\n"*2
        printf "\n#{dep} is an important dependancy.\n"
        exit
    end
end

create_makefile("ifp")

```

I solved that problem by simple commenting out the whole check statement they have there. This seemed to work and I was able to get a makefile. However, once I compiled and installed the binary the moment I tried to use the most basic function from the library, the one that initializes a new player class, it failed. Here's the irb session
```

>> require 'ifp'
=> true
>> player = IFP::Player.new
irb1.8: symbol lookup error: /usr/local/lib/site_ruby/1.8/i486-linux/ifp.so: undefined symbol: usb_init

```

From what I understand of symbol lookup errors, they generally happen when a program is built against the wrong version of a library. I have the newest libusb, libusb-0.1.12-2. I guess my question is two fold. First can anyone else replicate this error, because if so then its probably due to the library requiring an earlier version of libusb (the documentation was not specific as to which version to use). Second, if I'm the only one getting this error, what am I doing wrong?

~Andrew S.

---

