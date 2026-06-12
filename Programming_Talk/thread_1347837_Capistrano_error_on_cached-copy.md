---
title: "Capistrano error on cached-copy"
date: 2009-12-06
forum: Programming Talk
---

### Post by josh6847 on 2009-12-06
I am receiving the following error when running a cap deploy:update

failed: "sh -c 'if [ -d /home/deployer/apps/all_bout_texas/shared/cached-copy ]; then cd /home/deployer/apps/all_bout_texas/shared/cached-copy && git fetch -q origin && git reset -q --hard 2350e98662e7fe00d526ff5f69460beb868a978a && git clean -q -d -x -f; else git clone -q --depth 1 [email]git@github.com:jpowell/all_bout_texas.git[/email] /home/deployer/apps/all_bout_texas/shared/cached-copy && cd /home/deployer/apps/all_bout_texas/shared/cached-copy && git checkout -q -b deploy 2350e98662e7fe00d526ff5f69460beb868a978a; fi'"

Here is my deploy.rb:

set :application, "all_bout_texas"

# If you aren't deploying to /u/apps/#{application} on the target
# servers (which is the default), you can specify the actual location
# via the :deploy_to variable:
set :deploy_to, "/home/deployer/apps/#{application}"

# If you aren't using Subversion to manage your source code, specify
# your SCM below:
default_run_options[:pty] = true
set :scm, :git
set :repository, "git@github.com:jpowell/all_bout_texas.git"
set :deploy_via, :remote_cache
set :branch, "master"
set :git_shallow_clone, 1
set :copy_cache, true

# abt
role :app, "174.143.241.236"
role :web, "174.143.241.236"
role :db,  "174.143.241.236", :primary => true

set :scm_username, "my_user"
set :scm_passphrase, "my_pass"
set :scm_verbose, false

set :user, "my_user"
set :runner, "my_user"

namespace :deploy do 
    task :copy_database_configuration do 
    production_db_config = "/home/deployer/config/abt_database.yml" 
    run "cp #{production_db_config} #{release_path}/config/database.yml" 
  end
  
  desc "Restarting mod_rails with restart.txt"
  task :restart, :roles => :app, :except => { :no_release => true } do
    run "touch #{current_path}/tmp/restart.txt"
  end

  [:start, :stop].each do |t|
    desc "#{t} task is a no-op with mod_rails"
    task t, :roles => :app do ; end
  end
   
after "deploy:update_code", "deploy:copy_database_configuration" 
after "deploy:update_code", "deploy:restart"

end 

Any ideas? Thanks.

Josh

---

