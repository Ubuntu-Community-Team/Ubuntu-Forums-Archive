---
title: "What's wrong with my RoR Cookieless Session Reasoning?"
date: 2008-08-08
forum: Programming Talk
---

### Post by moephan on 2008-08-08
Hello,

I am writing a mobile version of my site, meaning that I cannot rely on cookies being present in the browser. In order to enable cookieless sessions in rails, I have:

1. Uncommented config.action_controller.session_store = :active_record_store in enviornment.rb
2. ran rake db:sessions:create
3. Checked and saw that the sessions table was created, and for each page visited, a row is added to the database
4. Set config.action_controller.session = {:session_key => '_session_id', #secret in environment.rb
5. Set session:cookie_only => false in the application controller (application.rb)
6. Pass _session_id=session.session_id as a parameter in every form post, or hypertext link
7. Turn off cookies for the site in the browser
8. I turned off  #protect_from_forgery in application.rb

However, the session is never passed between pages. I am testing with two pages and a controller action. I start at the view for food/index, then go to the login page at the view for user/signin, this page has a form that posts to the action user/login which redirects back to food/index.

The log shows that the session paramaters are being passed, but the session is not being set from it for some reason:

```


Processing FoodController#index (for 127.0.0.1 at 2008-08-08 07:53:15) [GET]
  Session ID: 1e772223d559acbfc37be1801960264e
  Parameters: {"_session_id"=>"72ccc9b1aecb680b3f7b9b1f6433cb4b", "action"=>"index", "controller"=>"food"}
Rendering template within layouts/standard
Rendering food/index
Completed in 0.03040 (32 reqs/sec) | Rendering: 0.02081 (68%) | DB: 0.00000 (0%) | 200 OK [http://127.0.0.1/food?_session_id=72ccc9b1aecb680b3f7b9b1f6433cb4b]


Processing UserController#signin (for 127.0.0.1 at 2008-08-08 07:53:19) [GET]
  Session ID: 2d3ff2902e6f38713104977a6183f0b9
  Parameters: {"_session_id"=>"1e772223d559acbfc37be1801960264e", "action"=>"signin", "controller"=>"user"}
Rendering template within layouts/standard
Rendering user/signin
Completed in 0.05656 (17 reqs/sec) | Rendering: 0.04269 (75%) | DB: 0.00000 (0%) | 200 OK [http://127.0.0.1/user/signin?_session_id=1e772223d559acbfc37be1801960264e]


Processing UserController#login (for 127.0.0.1 at 2008-08-08 07:53:23) [POST]
  Session ID: 4ff2e3e4d5517903552d19806da0c922
  Parameters: {"commit"=>"Sing In", "_session_id"=>"2d3ff2902e6f38713104977a6183f0b9", "username"=>"rick", "action"=>"login", "controller"=>"user", "password"=>"xxxxx"}
  [4;36;1mUser Load (0.003350)[0m   [0;1mSELECT * FROM `moephan_users` WHERE ( username = 'rick' ) LIMIT 1[0m
  [4;35;1mUser Columns (0.004784)[0m   [0mSHOW FIELDS FROM `moephan_users`[0m
Redirected to http://127.0.0.1:3000/food?_session_id=4ff2e3e4d5517903552d19806da0c922
Completed in 0.06059 (16 reqs/sec) | DB: 0.00813 (13%) | 302 Found [http://127.0.0.1/user/login]


Processing FoodController#index (for 127.0.0.1 at 2008-08-08 07:53:23) [GET]
  Session ID: aae03318484fbf955139477e6b074257
  Parameters: {"_session_id"=>"4ff2e3e4d5517903552d19806da0c922", "action"=>"index", "controller"=>"food"}
Rendering template within layouts/standard
Rendering food/index
Completed in 0.01741 (57 reqs/sec) | Rendering: 0.00894 (51%) | DB: 0.00000 (0%) | 200 OK [http://127.0.0.1/food?_session_id=4ff2e3e4d5517903552d19806da0c922]

```

Am I missing a step? Is there a problem with my reasoning regarding how to configure this?

Thanks in advanced.

Cheers, Rick

---

