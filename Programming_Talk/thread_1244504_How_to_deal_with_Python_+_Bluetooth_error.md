---
title: "How to deal with Python + Bluetooth error?"
date: 2009-08-19
forum: Programming Talk
---

### Post by UbuKunubi on 2009-08-19
Hello!

I have a python program that runs on Ubuntu server 8.04 LTS, and sits in a perpetual loop....until it very randomly crashes out!

Sometimes it only stays up for 5 minutes, and then its fine for 10 hours+ 

The error that is thrown is:
bluetooth.btcommon.BluetoothError: (115, 'Operation now in progress')

I dont understand why its failing so randomly, but this is the first time I've EVER had to trap errors with python, and since the program needs to be simple and reliable am considering catching the error, waiting 25 seconds and trying again; simply because when the program is restarted all goes well (until it falls over again!)

I'd be gratefull for any advice anyone can throw at this.

All the best,
Ubu

---

