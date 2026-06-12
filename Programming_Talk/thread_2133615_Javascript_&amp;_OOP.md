---
title: "Javascript &amp; OOP"
date: 2013-04-08
forum: Programming Talk
---

### Post by uncleheinz on 2013-04-08
Hello,

I have a problem with javascript here.

What I am trying to do is following:
1) one of the methods of a class generates the HTML form;
2) form submit calls another method from that same class;

My current ***non-working*** solution is here:
```

function MyClass() {}

MyClass.prototype = {
    showForm: function() {
        var my_form = '<form action="javascript:' + this + '.doSomeThing();">'
            + '<input type="submit" value="Click Me" /\>'
            + '</form>';

        return my_form;
    },

    doSomeThing: function() {
        /* Some code here */
    }
};


window.onload = function() {
    var g = new MyClass();
    document.body.innerHTML = g.showForm();
};

```

This is the problematic line:
```

var my_form = '<form action="javascript:' + this + '.doSomeThing();">'

```

Being more specific: the value of an '*action*' attribute should be something else, but I'm running out of ideas about what I should put there.

One solution would be this: rewrite the whole program using only procedural code. But that doesn't sound very tempting, since I'm trying to build something much bigger than just a small code snippet.

---

### Post by zozzz on 2013-04-09
I don't know your real situation but I try.

```
<script type="text/javascript">         
    function MyClass() {}

    MyClass.prototype = {
        showForm: function() {
            var my_form = '<form action="javascript:g.doSomeThing();">'
                + '<input type="submit" value="Click Me" /\>'
                + '</form>';

            return my_form;
        },

        doSomeThing: function() {
            /* Some code here */
            alert("hello");
        }
    };

    var g = new MyClass();

    window.onload = function() {
        document.body.innerHTML = g.showForm();
    };
</script> 

```

I have created a global var g, in this way you can use it anywhere.

If you create the g var in a function you can use it only in that function (scope)

---

### Post by uncleheinz on 2013-04-09
Thanks for your advice, but I'm  afraid that global variable is not the best solution in this particular case.

I've made some changes in my code:
```


function MyClass() {
    this.form_id = 'form_' + Math.ceil(Math.random() * 99999);
}


MyClass.prototype = {
    showForm: function() {
        var that = this;

        var my_form = (
            '<form id="' + this.form_id + '">'
            + '<input type="hidden" name="dummy_element" /\>'
            + '<input type="submit" value="Click Me" /\>'
            + '</form>'
        );

        document.body.innerHTML += my_form;

        if(document.getElementById(this.form_id)) {
            document.getElementById(this.form_id).onsubmit = function(e) {
                that.doSomeThing();
                e.preventDefault();
            };
        }
    },

    doSomeThing: function() {
        /* Some code here */
        alert('Button was clicked!');
    }
};


window.onload = function() {
    var g = new MyClass();
    g.showForm();
};


```

This code works, but not smoothly enough.
Firts af all, this ***e.preventDefault()*** statement does't seem to work with IE. But I try to fix this later, because right now there is also another and more important problem.

Let's assume I create multiple MyClass objects:
```

window.onload = function() {
    var g = new MyClass();
    g.showForm();

    var w = new MyClass();
    w.showForm();
};

```

Now I have two independent forms. But the second problem I was talking about is also associated whith this ***e.preventDefault()*** statement. Thing is: it only works with with the first form and not with the ohter one. No matter how many forms I create, ***e.preventDefault()*** works only in one of them.

I have no idea where the bug is. The Error Console of Firefox is not complaining anything.

---

