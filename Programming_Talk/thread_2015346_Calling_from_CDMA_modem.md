---
title: "Calling from CDMA modem"
date: 2012-07-03
forum: Programming Talk
---

### Post by piball on 2012-07-03
Hi 

I am able to make a phone call from CDMA modem by start minicom program in the terminal and pass AT+CDV=phonenumber

How  ever i need to automate this process. When user fill form in the web  page, the phone number should be passed to minicom program and execute  AT+CDV=phonenumber to make a phone call

Once the call has been made, the receiver will terminate, we expect multiple requests and moderate traffic.

Please help me how may i automate this process?

 

Thank you.

---

### Post by Bodsda on 2012-07-03
> **piball said:**
> Hi 

I am able to make a phone call from CDMA modem by start minicom program in the terminal and pass AT+CDV=phonenumber

How  ever i need to automate this process. When user fill form in the web  page, the phone number should be passed to minicom program and execute  AT+CDV=phonenumber to make a phone call

Once the call has been made, the receiver will terminate, we expect multiple requests and moderate traffic.

Please help me how may i automate this process?

 

Thank you.

Use PHP for the form, take the inputted phone number, validate it and then use it in a shell_exec() call?

---

