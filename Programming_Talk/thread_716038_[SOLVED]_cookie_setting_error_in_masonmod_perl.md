---
title: "[SOLVED] cookie setting error in mason/mod_perl"
date: 2008-03-05
forum: Programming Talk
---

### Post by pjkoczan on 2008-03-05
So, I'm having a bit of trouble setting cookies in Mason/mod_perl. This problem also occurs in "normal" perl/CGI scripts, so the Mason bit is not the factor.

I recently upgraded my OS and Apache version on this particular web server. Before this, I could create and bake (put into outgoing headers) a cookie anywhere, even after printing headers (I know this is non-standard...don't hurt me, I didn't create this festering malignancy of a web-app). The cookie wouldn't be visible until the next page load, which could be dealt with.

Unfortunately, there's not an easy way in this application to simply say, "create and bake the cookie before printing headers" because there is an autohandler (for uniformity in page displays) that prints html and therefore prints headers before I can create the cookie, and everything fails.

```

<%args>
   $id
</%args>
<%init>
use CGI::Cookie;
#use Apache2::Cookie;

my $grad = $ARGS{grad};

#my $cookie = new Apache2::Cookie (
my $cookie = new CGI::Cookie (
  -name  => 'user_info',
  -value => $some_calculated value
  -path  => '/grad-app',
);

#$r->headers_out->set('Set-Cookie' => $cookie);
$cookie->bake;

</%init>

```

The commented-out portions are other things I tried. They didn't work either. I'm just wondering if there's a workaround somehow, one that would preferably be not be a terrible kludge. Thanks.

---

### Post by pjkoczan on 2008-03-05
And it just solved itself. I'm going to have to chalk this one up to transient mod_perl caching issues and black magic.

---

