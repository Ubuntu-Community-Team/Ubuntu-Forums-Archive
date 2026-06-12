---
title: "click on input element another hide input display"
date: 2015-03-03
forum: Programming Talk
---

### Post by vijay9 on 2015-03-03
i'm trying to create another input when click on input
here is code

        <div><input id="search" onclick="clik()" type="text" placeholder="search"/></div>
        <div><input class="place"  type="text" placeholder="place"/></div>
         <script>
            var search2 = document.getElementById("search");
            var a = document.getElemetntByClassName('place');
            function clik(){
                 search2.appendChild(a).style.display="block";
            }
        </script>
div> input{width: 200px;height: 25px;border-radius: 0;margin-bottom: 5px;border: 1px solid !important;}
div>input.place{display: none;}

---

### Post by coffeecat on 2015-03-04
Not a Tutorial

*Thread moved to **Programming Talk**.*

---

### Post by Dimarchi on 2015-03-05
Rather than trying to create a new element, your code seems to suggest that you are trying to toggle the visibility of the class "place" element. Some points:


[LIST]
[*]search2 is irrelevant due to you using the function in the onclick attribute: remove it. 
[*]You have a typo in var a line: it is document.getElementsByClassName. 
[*]a is an array-like object. Access it in that fashion. 
[/LIST]

It should work after that.

---

