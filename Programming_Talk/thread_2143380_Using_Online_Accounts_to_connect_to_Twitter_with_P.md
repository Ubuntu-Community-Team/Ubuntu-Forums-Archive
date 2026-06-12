---
title: "Using Online Accounts to connect to Twitter with Python"
date: 2013-05-08
forum: Programming Talk
---

### Post by puzzler995 on 2013-05-08
I'm working on a program in which needs to communicate with Twitter. I would like to use Ubuntu Online Acconts (with libaccounts and signon), but cannot get it to log in.

```
 manager = Accounts.Manager.new_for_service_type("microblogging")
 manager.connect("enabled-event", on_enabled_event)
 i = 0
 #see there is one and only one twitter account
 #This will be removed eventually
 for account_service in manager.get_enabled_account_services():
     if account_service.get_account().get_provider_name() == "twitter":
         i = i + 1
 if i == 0:
     alert_send("Sorry, anonymous mode not supported yet, please sign into "
         "Twitter using Online Accounts", 2)
     sys.exit(0)
 elif i == 1:
     #Get the AccountService
     for account_service in manager.get_enabled_account_services():
         if account_service.get_account().get_provider_name() == "twitter":
             twitter_service = account_service
 

     #Get the authentication Information
     auth_data = twitter_service.get_auth_data()
     identity = auth_data.get_credentials_id()
     session_data = auth_data.get_parameters()
 

     #Create an authentication session
     auth_session = Signon.AuthSession.new(identity, auth_data.get_method())
 

     def login_cb(self, session, reply, error, user_data):
         if error:
             print(("Got authentication error:", error.message))
             return
         print(("login finished; reply: %s", (reply,)))
 

         if "AccessToken" in reply:
             access_token = reply["AccessToken"]
         return access_token
 

     auth_session.process(session_data, auth_data.get_mechanism(), login_cb,
         None)


```

When it runs, I get no error code, but no log-in confirmation either. I have a twitter account on my system.
Thanks!
Puzzler995

EDIT: BTW, this isn't the full code, I have the on_enabled_event method straight from the tutorial

---

