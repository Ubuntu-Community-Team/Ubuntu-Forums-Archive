---
title: "Improving this Python Code"
date: 2015-05-12
forum: Programming Talk
---

### Post by branau on 2015-05-12
Hey guys, I've been working on the first programming challenge found [here]("http://www.python-forum.org/viewtopic.php?f=10&t=378"), and I've finally got a fully functional first draft. I've only studied Python for about a month or so, so please tear this apart and tell me how I can improve it. I'm looking for any sort of feedback, really. Also, if you'd like to run it and try to make it crash, I'd appreciate that too. As you can see, I tried to handle all of the exceptions I could think of but I'm sure there could be more.

```
# Create a text-based menu system. An Inventory. Buy items from menu, 
# increase inventory, decrease 'store' inventory. Sell items from menu, decrease inventory, 
# increase 'store' inventory.

inventory = {'gold':100}
store_inventory = {'apple':10, 'banana':10, 'coconut':5, 'date':15, 'elderberry':30, 'fig':15, 'gold':500}
prices = {'apple':10, 'banana':10, 'coconut':5, 'date':15, 'elderberry':30, 'fig':15}

def display_store_inventory():
    nice_store_inventory = []
    store_gold = store_inventory['gold']
    store_items_only = {}
    for k, v in store_inventory.iteritems():
        if v > 0:
            store_items_only[k] = v
    del store_items_only['gold']
    for k, v in store_items_only.iteritems():
        nice_store_inventory.append("%s : %d" % (k, v))
    nice_store_inventory = [i.capitalize() for i in nice_store_inventory]
    print "-" * 80
    print "Store Gold: %d" % store_gold
    print "-" * 80
    if len(nice_store_inventory) < 1:
        print "The store has nothing in their inventory!"
    elif len(nice_store_inventory) == 1:
        print "The store's inventory is: ", ' '.join(nice_store_inventory)
    else:
        print "The store's inventory is: ", ', '.join(nice_store_inventory)
    print "-" * 80
    nice_store_inventory = []
    
def display_inventory():
    nice_inventory = []
    your_gold = inventory['gold']
    your_items_only = {}
    for k, v in inventory.iteritems():
        if v > 0:
            your_items_only[k] = v
    del your_items_only['gold']
    for k, v in your_items_only.iteritems():
        nice_inventory.append("%s : %d" % (k, v))
    nice_inventory = [i.capitalize() for i in nice_inventory]
    print "-" * 80
    print "Your Gold: %d" % your_gold
    print "-" * 80
    if len(nice_inventory) < 1:
        print "You have nothing in your inventory!"
    elif len(nice_inventory) == 1:
        print "Your inventory is: ", ' '.join(nice_inventory)
    else:
        print "Your inventory is: ", ', '.join(nice_inventory)
    print "-" * 80
    nice_inventory = []

def display_prices():
    nice_prices = []
    for k, v in prices.iteritems():
        nice_prices.append("%s : $%d/piece" % (k, v))
    nice_prices = [i.capitalize() for i in nice_prices]
    print "-" * 80
    for product in nice_prices:
        print product 
    print "-" * 80

def get_price(item, quantity):
    item = str(item)
    price = int(prices[item]) * int(quantity)
    return price

def increase_store_inventory(item, quantity, price):
    item = str(item)
    quantity = int(quantity)
    price = int(price)
    try:
        store_inventory[item] += quantity
    except KeyError:
        store_inventory[item] = quantity
    store_inventory['gold'] -= price
    
def decrease_store_inventory(item, quantity, price):
    item = str(item)
    quantity = int(quantity)
    price = int(price)
    store_inventory[item] -= quantity
    store_inventory['gold'] += price

def increase_inventory(item, quantity, price):
    item = str(item)
    quantity = int(quantity)
    price = int(price)
    try:
        inventory[item] += quantity
    except KeyError:
        inventory[item] = quantity
    inventory['gold'] -= price

def decrease_inventory(item, quantity, price):
    item = str(item)
    quantity = int(quantity)
    price = int(price)
    inventory[item] -= quantity
    inventory['gold'] += price

def buy_from_store(item):
    if item[-1] == "y":
        grammatically_correct_item = item.replace('y', 'ie')
    else:
        grammatically_correct_item = item
    quantity = raw_input("How many %ss would you like to buy?\n>>> " % grammatically_correct_item)
    while True:
        try:
            quantity = int(quantity)
        except ValueError:
            print "\033[1;31mOops! It looks like you didn't enter a number. Please try again.\033[1;m"
            quantity = raw_input("How many would you like to buy?\n>>> ")
        else:
            break
    if quantity > store_inventory[item]:
        print "\033[1;31mThe store doesn't have that many %ss.\033[1;m" % grammatically_correct_item
        prompt_user()
    else:
        total = get_price(item, quantity)
        if total < inventory['gold']:
            confirm = raw_input("\033[1;33mThe total cost of this purchase will be $%d. Are you sure you want to make the purchase?\033[1;m\n>>> " % total)
            if 'y' in confirm:
                decrease_store_inventory(item, quantity, total)
                increase_inventory(item, quantity, total)        
                prompt_user()
            else:
                prompt_user()
        else:
            print "\033[1;31mYou don't have enough gold for that. Try selling some of your inventory first.\033[1;m"
            prompt_user()

def sell_to_store(item):
    if item[-1] == "y":
        grammatically_correct_item = item.replace('y', 'ie')
    else:
        grammatically_correct_item = item
    quantity = raw_input("How many %ss would you like to sell?\n>>> " % grammatically_correct_item)
    while True:
        try:
            quantity = int(quantity)
        except ValueError:
            print "\033[1;31mOops! It looks like you didn't enter a number. Please try again.\033[1;m"
            quantity = raw_input("How many would you like to sell?\n>>> ")
        else:
            break
    if quantity > inventory[item]:
        print "\033[1;31mYou don't have that many %ss.\033[1;m" % grammatically_correct_item
        prompt_user()
    else:
        total = get_price(item, quantity)
        if total < store_inventory['gold']:
            confirm = raw_input("\033[1;33mThe total cost of this sale will be $%d. Are you sure you want to make the sale?\033[1;m\n>>> " % total)
            if 'y' in confirm:
                increase_store_inventory(item, quantity, total)
                decrease_inventory(item, quantity, total)        
                prompt_user()
            else:
                prompt_user()
        else:
            confirm = raw_input("\033[1;33mThe total cost of this sale will be $%d. The store only has $%d. Are you sure you want to make the sale?\033[1;m\n>>> " % (total, store_inventory['gold']))
            if 'y' in confirm:
                total = abs(store_inventory['gold'] - total)
                increase_store_inventory(item, quantity, store_inventory['gold'])
                decrease_inventory(item, quantity, total)        
                prompt_user()
            else:
                prompt_user()
def prompt_user():
    display_inventory()
    display_store_inventory()
    display_prices()
    choice = raw_input('What would you like to do?\n>>> ')
    choice = choice.lower()
    if 'buy' in choice:
        if len(store_inventory) > 1:
            item = raw_input("What would you like to buy?\n>>> ")
            item = item.lower()
            try:
                store_inventory[item]
            except KeyError:
                print "\033[1;31mThe store doesn't have that for sale.\033[1;m"
                prompt_user()
            else:
                buy_from_store(item)
        else:
            print "\033[1;31mThe store has nothing for you to buy!\033[1;m"
            prompt_user()
    elif 'sell' in choice:
        if len(inventory) > 1:
            item = raw_input("What would you like to sell?\n>>> ") 
            item = item.lower()
            try:
                store_inventory[item]
            except KeyError:
                print "\033[1;31mYou don't have that in your inventory.\033[1;m"
                prompt_user()
            else:
                sell_to_store(item)
        else:
            print "\033[1;31mYou have nothing to sell!\033[1;m"
            prompt_user()
    else:
        print "\033[1;31mHmm, I'm not quite sure what you meant by that. Try typing 'buy' or 'sell'\033[1;m"
        prompt_user()
    
prompt_user()
```

---

### Post by ofnuts on 2015-05-12
Several things from diagonal reading:

1) you are using "print" a bit inconsistently, sometimes with plain abuttal, sometimes with the better "%-substitution"
2) when I see price=int(price) used that many times, I wonder if you couldn't get you price right originally
3) prompt_user() calls itself recursively. This should really be an infinite loop calling prompt_user() and your code would return from prompt_user() instead of calling itself recursively.

---

### Post by branau on 2015-05-12
> **ofnuts said:**
> 1) you are using "print" a bit inconsistently, sometimes with plain abuttal, sometimes with the better "%-substitution"

I'm not quite sure what you're referring to here. Can you give me an example please?

> **ofnuts said:**
> 2) when I see price=int(price) used that many times, I wonder if you couldn't get you price right originally

Yeah, for some reason, whenever I tried to call that function from the other functions, it wasn't computing right. It was taking the number I tried to pass as an argument as a string, so then instead of multiplying my integers together, I was just getting that string multiplied by the number of items there were in the inventory. Any ideas on how I could prevent that?

> **ofnuts said:**
> 3) prompt_user() calls itself recursively. This should really be an infinite loop calling prompt_user() and your code would return from prompt_user() instead of calling itself recursively.

Just to make sure that I'm understanding you, if I were to add this at the end of the script:
```

while True:
    prompt_user()

```
and then remove all of the calls to prompt user, that would be better? Or should I write a new function that contains this loop and then call that function?

---

### Post by user1397 on 2015-05-13
when I tried to run it, I got this error:

[FONT=monospace][COLOR=#000000]File "test.py", line 127[/COLOR]
    else:
       ^
SyntaxError: invalid syntax
[/FONT]

---

### Post by ofnuts on 2015-05-13
> **William_Brawner said:**
> I'm not quite sure what you're referring to here. Can you give me an example please?



Yeah, for some reason, whenever I tried to call that function from the other functions, it wasn't computing right. It was taking the number I tried to pass as an argument as a string, so then instead of multiplying my integers together, I was just getting that string multiplied by the number of items there were in the inventory. Any ideas on how I could prevent that?



Just to make sure that I'm understanding you, if I were to add this at the end of the script:
```

while True:
    prompt_user()

```
and then remove all of the calls to prompt user, that would be better? Or should I write a new function that contains this loop and then call that function?

1) 
```

print 'There are %s apples in your basket' % apples

``` 

2) Well, you have to find that reason.... Coercing the types all over the place isn't good; You can use type(variable) to find the type a variable, but there is no reason why your prices cannot remain integers and your items names strings.

3) Instead of 

```

def prompt_user:
   [:...]
   prompt_user()

prompt_user()

```
do
```

def prompt_user:
   [:...]
   return True  # or "return False" to exit....

while prompt_user():
   pass; # or some trace instruction

```

---

### Post by branau on 2015-05-13
> **ubuntuman001 said:**
> when I tried to run it, I got this error:

[FONT=monospace][COLOR=#000000]File "test.py", line 127[/COLOR]
    else:
       ^
SyntaxError: invalid syntax
[/FONT]

The file worked fine on my computer so I tried copy/pasting it to a  new file and running it and I got the same result. Turns out it erased  some of my spaces when I copied/pasted it from the original file to  here, so I fixed the indentation errors that came up from the text here.

> **ofnuts said:**
> 1) 
```

print 'There are %s apples in your basket' % apples

```

Sorry, I should've been more specific. Could you give me an example from my code where I did that? There were some parts where, to keep it grammatically correct, I avoided using that substitution but I tried to use it wherever I could.

> **ofnuts said:**
> 2) Well, you have to find that reason.... Coercing the types all over the place isn't good; You can use type(variable) to find the type a variable, but there is no reason why your prices cannot remain integers and your items names strings.

Alright, I'll take a look at the code again and see where I can get that to work without having to constantly declare it as an integer.

> **ofnuts said:**
> 3) Instead of 

```

def prompt_user:
   [:...]
   prompt_user()

prompt_user()

```
do
```

def prompt_user:
   [:...]
   return True  # or "return False" to exit....

while prompt_user():
   pass; # or some trace instruction

```

How does this look?
```
while True: 
    prompt_user()
```

---

### Post by ofnuts on 2015-05-13
> **William_Brawner said:**
> 
```
while True: 
    prompt_user()
```

Not really the same, because this forces you to exit the program from within prompt_user(). That can be OK now, but sometime later you find you need cleanu action when you exit the program (cloing database connexions, or else) and then calling this from prompt_user() isn't very clean.

---

### Post by user1397 on 2015-05-13
> **William_Brawner said:**
> The file worked fine on my computer so I tried copy/pasting it to a  new file and running it and I got the same result. Turns out it erased  some of my spaces when I copied/pasted it from the original file to  here, so I fixed the indentation errors that came up from the text here.
Ah yup you are correct, ran it again and now it works.  Nifty program, I am learning python myself so anything new is always interesting.

---

### Post by branau on 2015-05-13
> **ubuntuman001 said:**
>  I am learning python myself so anything new is always interesting.

I also posted this request on a Python-specific forum and one of the moderators gave me a ton of stuff to work with, you might find [this]("http://www.python-forum.org/viewtopic.php?f=6&t=15672") interesting too.

---

### Post by user1397 on 2015-05-14
> **William_Brawner said:**
> I also posted this request on a Python-specific forum and one of the moderators gave me a ton of stuff to work with, you might find [this]("http://www.python-forum.org/viewtopic.php?f=6&t=15672") interesting too.
thanks!

---

