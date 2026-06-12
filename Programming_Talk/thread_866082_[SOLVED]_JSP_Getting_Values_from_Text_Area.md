---
title: "[SOLVED] JSP: Getting Values from Text Area"
date: 2008-07-21
forum: Programming Talk
---

### Post by balagosa on 2008-07-21
let's say I have two files. page1.jsp and page2.jsp.

in page1.jsp I have a textarea with **name="tArea", a button which will submit TextArea information** to page2.jsp as parameters.

on page2.jsp I will get that value that is being passed and I will print it out via **String strTArea = request.getParameter("tArea");out.println(strTArea);**

The problem comes when the parameter passed involves "carriage return" and "line feed". I can verify on the address bar that the parameter passed has the correct amount of "enters". but when I get the value via "request.getParameter()", the data is malformed turning "enters" into mere spaces.

(enter = line feed + carriage return)

So, anyone has encountered the same problem? Might want to help me out because I need the correct data from that parameter. Any ideas are welcome.

---

### Post by balagosa on 2008-07-21
[Java Website]("http://forums.sun.com/thread.jspa?forumID=45&threadID=705997") helped me with this problem.

---

