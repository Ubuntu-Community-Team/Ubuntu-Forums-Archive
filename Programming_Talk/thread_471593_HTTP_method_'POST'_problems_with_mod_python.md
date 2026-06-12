---
title: "HTTP method 'POST' problems with mod_python"
date: 2007-06-12
forum: Programming Talk
---

### Post by lrhaugen on 2007-06-12
Hi,

Have anyone experienced problems when using POST method to mod_python scripts?

from mod_python import apache
from mod_python import util

def index(req):

        form = util.FieldStorage(req)
        fname = form.getfirst("firstname","None")

'fname' will output "None" when the request is POST, but will output a value when the request is GET. I have seen the questions in some other forums, but no answers.

Thanks!

---

