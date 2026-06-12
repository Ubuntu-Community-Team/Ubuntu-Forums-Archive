---
title: "Bluefish Editor and Preview Brower button in Ubuntu 12.04LTS not working"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by noteleks on 2014-05-11
I am trying to learn how to use Bluefish editor. But cannot get pass being able to preview my page in Firefox. I have read some troubleshooting but none of it has helped. When I click on "Preview in Browser" button at the top in the menu bar nothing happens. I even have my Firefox open hoping that would work. Please advise. 

P.S. Bluefish Editor is 2.2

---

### Post by Dennis N on 2014-05-11
The button doesn't work in my somewhat older version either. 

To View Page You are Making:

Method 1 -
In practice, You can just save the page in a working folder, then open the page in Firefox (or other browser) and leave Firefox open with the page for updating. As you edit the page and want to see the result, save it, switch to Firefox and reload. Then switch back to the editor as needed.

Method 2 -
It is possible to open the page from **External > (choose browser in drop down)**. That works if the browser is listed, and configured. To get it listed and configured, use **Edit > Preferences > External Programs > Broswers** and add the Name and command to start the browser, then press Apply. The page still needs to be saved to disk before it will open. 

For Firefox, I see:

Name: Firefox
Command: /usr/bin/firefox %s&

I never saw the point in doing this, as Method 1 always worked quite well for me. Sorry if the menu locations might have changed in your Bluefish version.

---

### Post by noteleks on 2014-05-11
Thank you for your reply. I will use Method 1 as well.

---

