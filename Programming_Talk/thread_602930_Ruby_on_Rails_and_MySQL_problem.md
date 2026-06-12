---
title: "Ruby on Rails and MySQL problem"
date: 2007-11-04
forum: Programming Talk
---

### Post by pixelnate on 2007-11-04
I am trying to do a simple script/generate model... and I cannot figure out what the error is trying to tell me. Can somebody help me decipher this, please?

```

pixelnate@silverbuntu:~/projects/1050_UAI_Website/uai$ script/generate model Product
/usr/lib/ruby/1.8/yaml.rb:133:in `load': syntax error on line 18, col 2: `  socket: /var/run/mysqld/mysqld.sock' (ArgumentError)
        from /usr/lib/ruby/1.8/yaml.rb:133:in `load'
        from ./script/../config/../vendor/rails/railties/lib/initializer.rb:551:in `database_configuration'
        from ./script/../config/../vendor/rails/railties/lib/initializer.rb:234:in `initialize_database'
        from ./script/../config/../vendor/rails/railties/lib/initializer.rb:92:in `process'
        from ./script/../config/../vendor/rails/railties/lib/initializer.rb:47:in `send'
        from ./script/../config/../vendor/rails/railties/lib/initializer.rb:47:in `run'
        from ./script/../config/../config/environment.rb:13
        from /home/pixelnate/projects/1050_UAI_Website/uai/vendor/rails/railties/lib/commands/generate.rb:1:in `require'
        from /home/pixelnate/projects/1050_UAI_Website/uai/vendor/rails/railties/lib/commands/generate.rb:1
        from script/generate:3:in `require'
        from script/generate:3
pixelnate@silverbuntu:~/projects/1050_UAI_Website/uai$ 

```

I really have no idea where to go. Anybody else have this same kind of problem?

:confused:

---

### Post by PhilMcRevis on 2008-03-31
I'm having the exact same problem, any suggestions?

---

### Post by pixelnate on 2008-04-01
It means that the database.yml isn't set up correctly. I cannot tell you what I did to fix it, except to say that you should make sure you have the correct socket listed, or perhaps even take the socket info off and just use the "host: localhost" to tell your dev machine where to find the database.

It could be that you don't have mysql set up properly. If you are just getting started with Rails you should probably start with Rails 2 and use it's default db: sqlite. Otherwise, you may need to reinstall mysql.

FYI, my setup is currently working with the socket set to "/var/run/mysqld/mysqld.sock".

I hope that helps.

---

### Post by pradeepkrishnan on 2010-03-19
I had an empty password for the user account and ran into this problem. Well, the application was working as such but the scaffolding was failing with this same problem. Luckily tried to remove a space in front of the password: param and this was the line "password:" and no space.

---

