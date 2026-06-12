---
title: "Apache2/Modpython/Python question"
date: 2009-02-04
forum: Programming Talk
---

### Post by abeisgreat on 2009-02-04
ok a quick google search turned up nothing, I know this will be real simple, but how can I read POST and GET data sent to my py script on my server?

EDIT: FOUND!

```

from mod_python import apache
from mod_python.util import parse_qsl


options = {"content_type": "text/plain"}

#Code Via http://dresstosurvive.wordpress.com

def index(req):
    req.add_common_vars()
    req.content_type    = options['content_type']
    query               = req.subprocess_env['QUERY_STRING']
    query               = parse_qsl(query)
    return query



```

Thanks abe

---

