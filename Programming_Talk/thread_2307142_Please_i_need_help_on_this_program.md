---
title: "Please i need help on this program"
date: 2015-12-22
forum: Programming Talk
---

### Post by 4TTLehMaTZ on 2015-12-22
[B]Please i'm new to python programming and i need help on this program;

Create a class called BankAccount[/B]


[LIST]
[*]Create a constructor that takes in an integer and assigns this to a `balance` property.
[*]Create a method called `deposit` that takes in cash deposit amount and updates the balance accordingly.
[*]Create a method called `withdraw` that takes in cash withdrawal amount and updates the balance accordingly. if amount is greater than balance return `"invalid transaction"`
[*]Create a subclass MinimumBalanceAccount of the BankAccount class
[/LIST]


Here is what i did:
#BankAccount.py

 class BankAccount(object): 
def __init__(self, initial_balance=0):
        self.balance = initial_balance
    def deposit(self, amount):
        self.balance += amount
    def withdraw(self, amount):
        if amount > self.balance
        raise RuntimeError("invalid transaction")
        self.balance -= amount
    def overdrawn(self):
        return self.balance < 0
  class MinimumBalanceAccount(BankAccount):
    def __init__(self, minimum_balance):
        BankAccount.__init__(self)
        self.minimum_balance = minimum_balance
my_account = BankAccount(15)
my_account.withdraw(5)
print my_account.balance

---

### Post by ian-weisser on 2015-12-22
Please use [code] tags for your code, to keep the indenting.

This seems a lot like a homework assignment.
You have one syntax error.

---

### Post by QIII on 2015-12-22
When is this due?

---

### Post by 4TTLehMaTZ on 2015-12-22
yes. its homework. i keep getting errors as i execute the code. what do you mean by [code] tags? i'm new to programming. i would appreciate if you could explain.

---

### Post by slickymaster on 2015-12-22
@centvictor:
_Regarding code tags:_
Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

_The reason why I'm closing your thread:_
In the  the [code of conduct]("http://ubuntuforums.org/misc.php?do=showrules"), to which you agreed to when you created your account, there's a link in the eighth paragraph that points to the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945") thread, which states in its eighth point the following:> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

---

