---
title: "Any curl experts?  Having trouble using curl with aspx"
date: 2010-04-12
forum: Programming Talk
---

### Post by dwasifar on 2010-04-12
Trying to use curl to automate some form-filling tasks on phonepower.com's website, which is all .aspx files.  This is how I'm trying to log in:

```
curl -c ~/Desktop/cookies.txt -d "ctl00$Account_ContentPlaceHolder$MyAccountLogin$UserName=MYUSERNAME&ctl00$Account_ContentPlaceHolder$MyAccountLogin$Password=MYPASSWORD&ctl00$Account_ContentPlaceHolder$MyAccountLogin$LoginButton=Login" https://secure.phonepower.com/Account/login.aspx
```

This sets a cookie, but I can see from the returned html that the login was actually not successful, and subsequent curl commands using that cookie are also not successful and redirect to a login page.  I'm not experienced with curl.  Is there anything obvious wrong with what I'm doing here?

---

