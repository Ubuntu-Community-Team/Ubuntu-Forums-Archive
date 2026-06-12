---
title: "Run perl"
date: 2008-02-07
forum: Programming Talk
---

### Post by anbumanij on 2008-02-07
How to run .html extension in perl document root. Now only .pl  and .cgi is running. Wht to do to run .html. at cgi-bin document root.

---

### Post by tr333 on 2008-02-07
If you want to display a simple HTML page inside the cgi-bin directory, you would have to either move the file out of the directory or provide a simple perl wrapper around the html.

```

use CGI;
print header;
print <<'EOI'

# HTML CODE HERE

EOI

# EOI is the end of the 'here document' surrounding the HTML text.'

```

There might be another way to configure apache to allow html and cgi together, but I don't know of any.

---

### Post by pmasiar on 2008-02-07
> **anbumanij said:**
> How to run .html extension in perl document root. Now only .pl  and .cgi is running. Wht to do to run .html. at cgi-bin document root.

Using Apache web server?

Please read "how to ask questions" in my sig.

---

