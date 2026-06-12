---
title: "[PHP] New Movie Voting Site"
date: 2009-11-10
forum: Programming Talk
---

### Post by elasolova on 2009-11-10
Today,I implemented a voting site on [http://javaist.com/moviemeter]("http://javaist.com/moviemeter") in PHP. There is no need to sign up to vote and a guest can vote as much as he wants. I did like this because once there was a soccer clicking game where the supporters for each team beat the opposing team as they continuously click on their team. So, in a way, if a person is very eager that a movie is good he can continuously rate it excellent. Anyway, I hope you like it and hope that it makes a decent list on good movies.

Best,
elasolova

---

### Post by 0cton on 2009-11-10
and the meaning of this thread is?
Also It's not that hard to make a script that will render human votes useless.
I would recommend to use POST instead of GET.
and Implement a CAPTCHA system if you don't want users to login/register/authenticate (It will prevent bots from voting )
ALSO your site(if it's yours) more precisely your php script doesn't test at all if the mark is a number or if it's even in the limits of 1-9
Are you using a database to store those values?
As well it does not inform if the id is out of range among others...
You should work more on it.

---

