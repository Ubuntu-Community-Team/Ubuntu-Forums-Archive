---
title: "Ruby On Rails Question"
date: 2006-02-20
forum: Programming Talk
---

### Post by bbqbaker on 2006-02-20
Hi, I am new to understanding rubies framework on rails and i have a question. for a typical website, lets take for example a car website similiar to autotrader, would there be 1 controller with 1 to many define methods?

for example: this website should have a user account section, search and display section, a details section for each car.

now would all of this functionality be under 1 controller? where each defined method passes information to other define methods? for example when searching for a particular type of automobile using a define called search, a display page will show each vehicle that matches 'honda' type. since this display output will also have a hidden field 'key' for each particular car, this 'key' will then need to be passed to the details button so the controller can get additional information about the car. now this 'details' button, is that another method defined under the same main controller that the defined search is at? or is 'details' another controller.

i am not sure if i am explaining myself correctly.

---

