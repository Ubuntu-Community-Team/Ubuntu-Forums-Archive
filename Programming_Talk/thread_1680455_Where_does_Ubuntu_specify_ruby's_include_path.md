---
title: "Where does Ubuntu specify ruby's include path?"
date: 2011-02-02
forum: Programming Talk
---

### Post by khughitt on 2011-02-02
Does anyone know how Ubuntu sets the default search path when require is called? Specifically, I am trying to figure out where the current working directory is included.

For example, using:

```
ruby -e 'puts $:'
```

to get a list of the search paths, on a vanilla 10.10 installation returns:

```

/usr/local/lib/site_ruby/1.8
/usr/local/lib/site_ruby/1.8/i686-linux
/usr/local/lib/site_ruby/1.8/i486-linux
/usr/local/lib/site_ruby
/usr/lib/ruby/vendor_ruby/1.8
/usr/lib/ruby/vendor_ruby/1.8/i686-linux
/usr/lib/ruby/vendor_ruby
/usr/lib/ruby/1.8
/usr/lib/ruby/1.8/i686-linux
/usr/lib/ruby/1.8/i486-linux
.

```

How does "." get included? None of the Ruby environmental variables listed in the ruby manpages seem to be set. I would like to try and configure another non-Ubuntu system similarly, and am curious how Ubuntu manages to configure this at a system-wide level.

Any insight would be appreciated :)

Thanks,
Keith

---

### Post by khughitt on 2011-02-02
Okay I was mistaken: it seems like Ubuntu does not do anything special, but rather I was simply using an older version of Ruby (1.8) for which "." was included in the $LOAD_PATH. In newer versions (1.9.2+) that is no longer the case: [http://stackoverflow.com/questions/2900370/why-does-ruby-1-9-2-remove-from-load-path-and-whats-the-alternative](http://stackoverflow.com/questions/2900370/why-does-ruby-1-9-2-remove-from-load-path-and-whats-the-alternative).

---

