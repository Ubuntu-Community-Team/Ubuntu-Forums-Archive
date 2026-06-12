---
title: "Howto: set up eclipse for Python with automatic build on save"
date: 2017-07-14
forum: Programming Talk
---

### Post by paulmilliken on 2017-07-14
[LIST=1]
[*]Download Eclipse installer from eclipse.org
[*]Run installer and choose the minimal version to download and install it
[*]Once Eclipse has installed and launches, go to "help"->"install new software"
[*]Work with "All available sites" and search for 'marketplace' and install
[*]Go to "help"->"eclipse marketplace".  Under "popular" select PyDev and install
[*]Go to "file"->"new project" and create a PyDev project.  It will ask if you want to use the Python perspective.  Click yes and remember decision
[*]Right click on project and select properties
[*]Create a new builder with location="/usr/bin/python" and arguments = ${workspace_loc:/path/to/file.py}
[*]Under the "Build Options" tab, check "During auto builds" so tests will run every time a change is saved
[*]Make sure file.py has the following at the end:
```
if __name__ == "__main__":
    unittest.main()
```
[/LIST]

---

