---
title: "ubuntuone developer-id"
date: 2023-12-30
forum: New to Ubuntu
---

### Post by dkrinsky on 2023-12-30
I created a ubuntuone account, but do not seem to have a developer-id
how do I get one?

dkrinsky@dkrinsky-Precision-7670:~/rpi4/canonical$ snapcraft whoami
email: [email]dkrinsk@gmail.com[/email]
username: dkrinsky
id: None
permissions: package_access, package_manage, package_metrics, package_push, package_register, package_release, package_update
channels: no restrictions
expires: 2024-12-29T12:07:10.000Z

---

### Post by MAFoElffen on 2023-12-30
The instructions for that were written in 2019 and the links for that and how that is done has changed since then... Even if I to the Snap Craft main page and try to login... Those links are broken also. But the Snapcraft Developer Login page still works...

Once you have your Ubuntu One credentials... Then go to this link: [https://dashboard.snapcraft.io/stores/snaps/](https://dashboard.snapcraft.io/stores/snaps/)
Keep that link handy/saved somewhere.


Look in the top bar for "Login" > Select it to log in with your Ubuntu One credentials. Once Logged in, then select your "UserName" from where it replaced the Login link > Select Account Details...

From that page, check the checkbox for "I have read and accept the Developer Agreement" > Save Details by selecting the "Update My Account. Your account will be assigned a DeveloperID... after accepting that Developer Agreement)

You can retieve that ID two ways, either on your Snapcraft Dev Dashboard Account details page... Or
```

# Make sure you have this installed
sudo snap install snapcraft --stable

snapcraft login
# Enter your Ubuntu One Login details

snapcraft whoami
## Output from mine <sanitized>
#email: mafoelffen@[Sanitized]
#username: mafoelffen
#id: [Sanitized]
#permissions: package_access, package_manage, package_metrics, package_push, package_register, package_release, package_update
#channels: no restrictions
#expires: 2024-12-29T14:55:30.000Z                                               

snapcraft loggout

```

---

### Post by dkrinsky on 2024-01-02
Thanks very much.  The link and sign up instructions you provided worked.  I now have a developer id that is shown when I run the **snapcraft whoami** command.

---

