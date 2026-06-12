---
title: "Answering a call in android programmatically"
date: 2012-12-23
forum: Programming Talk
---

### Post by 3v3rgr33n on 2012-12-23
Hi

I've been workin' on an app over the past two days, the details are not really important. The app is going to answer some calls, depending whether they are in the database I created.

I've tried stackoverflow and non of the threads have what I want. I have a broadcast receiver inside my main activity for picking up the phone. So far, I can get the number which is calling -- I need to pick the phone, How do I do that?

Here's my onReceive() method from the broadcast receiver
```
        public void onReceive(Context context, Intent intent) {
            boolean isInDb = false;
            String state = intent.getStringExtra(TelephonyManager.EXTRA_STATE);
            if (state.equals(TelephonyManager.EXTRA_STATE_RINGING)){
                Toast.makeText(getApplicationContext(), "Ringing", Toast.LENGTH_LONG).show();
                String num = intent.getStringExtra(TelephonyManager.EXTRA_INCOMING_NUMBER);
                //check if number is in db
                    //isInDb = true;
                    //answer call
              //else do nothing
            }
            else if (state.equals(TelephonyManager.EXTRA_STATE_IDLE)){
                Toast.makeText(getApplicationContext(), "IDLE", Toast.LENGTH_LONG).show();
            }
            else{
                Toast.makeText(getApplicationContext(), "Offhook", Toast.LENGTH_LONG).show();
                if (isInDb){
                    //Do something cool
                }
            }
        }
```

---

### Post by CptPicard on 2012-12-23
Answering and making calls sounds exactly like the sort of functionality I would not even allow to happen programmatically if I were designing a mobile device API. You really need real user confirmation on a case by case basis...

---

### Post by 3v3rgr33n on 2012-12-31
After days of googling and trying out different hacks, I give up.
It's not possible.

---

