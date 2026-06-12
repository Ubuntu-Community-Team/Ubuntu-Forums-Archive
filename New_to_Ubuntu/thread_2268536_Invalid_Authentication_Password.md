---
title: "Invalid Authentication Password"
date: 2015-03-09
forum: New to Ubuntu
---

### Post by mapleserum on 2015-03-09
I keep getting this same prompt whenever I try to do something:

Authentication Required
To install or remove programs you need to Authenticate.

or if I try to change user data

Authentication Required
To change user data you need to authenticate.

I am given the option to Authenticate or Cancel

Seems appropriate. But the problem is that it doesn't accept the password that I have set for my user account. I have tried every possible password on this prompt with no success. 1)I do not remember setting an authentication password, 2) I have only had ubuntu for a day after 20 years of windows, 3) I have installed gnome shell, 4) It won't accept my password in terminal either (it doesn't respond when i hit a character) 5) I know nothing about terminal and would need a really simple walkthrough if someone knows how to fix the problem through terminal.

I am hoping someone is able to help me through this.
Much love.

---

### Post by slickymaster on 2015-03-09
Hi mapleserum, welcome to the forums.

Just reset your password. See this easy to follow tutorial on it: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Impavidus on 2015-03-11
1: It's the same password you set for the first account you created when installing Ubuntu. The user you create during installation by default has permission to install programs etc. When you have logged in using that user account, you can use that user's password to authenticate. Slickymaster provided a link to reset the password. On rare occasions there may be a problem with keyboard layout.
2: That means you have to unlearn 20 years of Windows experience.
3: Which GUI you use shouldn't really matter (not in this case at least).
4: This is normal. When you type your password in the terminal, no feedback is provided. It doesn't even show ****. The input however is registered, so if you type the correct password and hit enter it should be accepted.
5: You don't really need the terminal on Ubuntu, but often it provides the easiest (but maybe not the only) way to solve a problem. That's why we often suggest terminal commands. And of course, some people simply like the terminal.

---

