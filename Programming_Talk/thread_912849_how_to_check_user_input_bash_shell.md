---
title: "how to check user input bash shell"
date: 2008-09-07
forum: Programming Talk
---

### Post by CheeSen on 2008-09-07
can i know how to check user input ? And make sure only alphabetic characters and spaces .
any idea?

---

### Post by mssever on 2008-09-07
> **CheeSen said:**
> can i know how to check user input ? And make sure only alphabetic characters and spaces .
any idea?
```
if [[ $user_input =~ ^[a-zA-Z ]+$ ]]; then
    echo "Good user. Here's a cookie."
else
    echo "You didn't enter what I told you to enter. Go to your room."
fi
```Note that this is Bash-specific. If you call your script with sh, it will fail.

---

### Post by ghostdog74 on 2008-09-07
check the bash link in the sig. all the questions that you have posted in other forums including this one can be found in that link.

---

