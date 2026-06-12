---
title: "Installing Perl Modules CPAN"
date: 2005-08-29
forum: Programming Talk
---

### Post by MeanRoy on 2005-08-29
I just Installed Ubuntu, I had RedHat ver 8.0. Ubuntu installed smoothly with no problems whatsoever. Needless to say, I'm impressed. Very nice.

Now to the problem:

I tried to use Andreas König's CPAN module to install some Perl modules which apparently weren't included in the distribution.

Specifically, URI::Escape. Install failed, apparently because make failed.
I went on and tried to get libwww-perl same/similar problem.

Can anyone give me some clues as to how to fix the problem, or barring that, where I should be asking the question?

I am a fresh newby on Ubuntu, with only a little familiarity with Unix/Linux, thus I would prefer to use this automated system of installing Perl modules.

I have been learning Perl for a while and have modest proficiency. I got the Windows version installed without a problem, but it's a binary. 

Roy.

PS, as I write this I realize I was not logged in as root. I'll try again as root, and post the result here.

OK, I'm back. Tried as root, same result.
```
Failed Test          Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
base/message.t                     92    2   2.17%  83 86
html/form-param.t       2   512    24   48 200.00%  1-24
html/form.t             2   512   103  206 200.00%  1-103
local/autoload-get.t                1    1 100.00%  1
local/autoload.t                    1    1 100.00%  1
local/get.t             2   512     2    4 200.00%  1-2
local/http-get.t                   20    6  30.00%  1-2 5-7 20
local/http.t                       18    6  33.33%  1-2 5-7 18
robot/ua-get.t                      8    2  25.00%  3 5
robot/ua.t                          7    2  28.57%  3 5
Failed 10/30 test scripts, 66.67% okay. 149/759 subtests failed, 80.37% okay.
make: *** [test] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force
```

---

### Post by stoffe on 2005-08-29
You could install libwww-perl and liburi-perl via synaptic or apt, it's usually easier to try and get perl modules that way whenever possible (like everything else).

---

### Post by MeanRoy on 2005-08-29
Thanks, I just found synaptic and checked off the modules I could locate between  posting the question and reading the answer..

I just tried my script. It's running!

Very cool. I'd still like to get CPAN to work, it's probably one of the things I let it "guess".

Roy.

--- edit ---

Now if I figure out how to run my scripts with cron I won't have to play with Windows Task Scheduler anymore!

---

### Post by rwabel on 2005-09-01
I needed some cpan stuff for compiling filer. maybe my howto in th wiki helps you: [https://wiki.ubuntu.com/Filer](https://wiki.ubuntu.com/Filer)

---

