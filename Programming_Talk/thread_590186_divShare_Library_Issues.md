---
title: "divShare Library Issues"
date: 2007-10-24
forum: Programming Talk
---

### Post by 71fnRVVm on 2007-10-24
For some reason, the class information keeps being printed onto the page...

I'm using the PHP4 Client Library to do this.  Not printing any of the divshare_lib processes in the page.

This code:
```

ds = new divshare_api('[key]','[secret]');
$api_session_key = $ds->login('[email]', '[password]');
$ticketer = $ds->get_upload_ticket();
$ticket = $ticketer['response']['upload_ticket'];
$ds->logout();
```

Prints out:
```

method=login&api_key=[key]&user_email=[email]&user_password=[password]
method=get_upload_ticket&api_key=[key]&api_session_key=828-40e91311365f&api_sig=358315e742064806ecccbca52553d574
method=logout&api_key=[key]

```

I'm using this to upload a video via a form, and then spit out some embed data and things.  All of this works.  It just, for some reason, keeps printing what I showed above for no reason that I can find.

Any help is appreciated.

[also seen at:  [http://groups.google.com/group/divshare-api/browse_thread/thread/939412f8f5ac8701]](http://groups.google.com/group/divshare-api/browse_thread/thread/939412f8f5ac8701])

Thanks
--Kyle

---

