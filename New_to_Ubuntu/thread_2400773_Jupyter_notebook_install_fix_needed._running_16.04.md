---
title: "Jupyter notebook install fix needed. running 16.04 lts"
date: 2018-09-10
forum: New to Ubuntu
---

### Post by infernalzeus on 2018-09-10
i need to follow the following commands to install
[I][run the below command

pip3 install jupyter

Then run the below command
~/.local/bin/jupyter-notebook

ctrl C * x

Then finally this

export PATH=~/.local/bin:$PATH


after this, if required 
jupyter notebook
]


**it gives me this**[/I][SIZE=1]
Collecting jupyter
  Using cached [https://files.pythonhosted.org/packages/83/df/0f5dd132200728a86190397e1ea87cd76244e42d39ec5e88efd25b2abd7e/jupyter-1.0.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/83/df/0f5dd132200728a86190397e1ea87cd76244e42d39ec5e88efd25b2abd7e/jupyter-1.0.0-py2.py3-none-any.whl)
Collecting nbconvert (from jupyter)
  Using cached [https://files.pythonhosted.org/packages/b5/bb/94c493051d60e5b9c0f7f9a368b324201818c1b1c4cae85d1e49a41846c7/nbconvert-5.4.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/b5/bb/94c493051d60e5b9c0f7f9a368b324201818c1b1c4cae85d1e49a41846c7/nbconvert-5.4.0-py2.py3-none-any.whl)
Collecting jupyter-console (from jupyter)
  Using cached [https://files.pythonhosted.org/packages/77/82/6469cd7fccf7958cbe5dce2e623f1e3c5e27f1bb1ad36d90519bc2d5d370/jupyter_console-5.2.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/77/82/6469cd7fccf7958cbe5dce2e623f1e3c5e27f1bb1ad36d90519bc2d5d370/jupyter_console-5.2.0-py2.py3-none-any.whl)
Collecting qtconsole (from jupyter)
  Using cached [https://files.pythonhosted.org/packages/ff/1f/b340d52dee46fbbe8a097dce76d1197258bb599692159d94c80921fef9eb/qtconsole-4.4.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/ff/1f/b340d52dee46fbbe8a097dce76d1197258bb599692159d94c80921fef9eb/qtconsole-4.4.1-py2.py3-none-any.whl)
Collecting ipykernel (from jupyter)
  Using cached [https://files.pythonhosted.org/packages/7a/de/a03a5c1f8b743675add3c98f1eb877c67bb29c5196ee6ce54e9c839d23cc/ipykernel-4.9.0-py3-none-any.whl](https://files.pythonhosted.org/packages/7a/de/a03a5c1f8b743675add3c98f1eb877c67bb29c5196ee6ce54e9c839d23cc/ipykernel-4.9.0-py3-none-any.whl)
Collecting notebook (from jupyter)
  Using cached [https://files.pythonhosted.org/packages/5e/7c/7fd8e9584779d65dfcad9fa2e09c76131a41f999f853a9c7026ed8585586/notebook-5.6.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/5e/7c/7fd8e9584779d65dfcad9fa2e09c76131a41f999f853a9c7026ed8585586/notebook-5.6.0-py2.py3-none-any.whl)
Collecting ipywidgets (from jupyter)
  Using cached [https://files.pythonhosted.org/packages/ea/c5/0482342559f0fd24909572fe00bb59b2bae98b22d90aac7950f51a98f555/ipywidgets-7.4.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/ea/c5/0482342559f0fd24909572fe00bb59b2bae98b22d90aac7950f51a98f555/ipywidgets-7.4.1-py2.py3-none-any.whl)
Collecting nbformat>=4.4 (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/da/27/9a654d2b6cc1eaa517d1c5a4405166c7f6d72f04f6e7eea41855fe808a46/nbformat-4.4.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/da/27/9a654d2b6cc1eaa517d1c5a4405166c7f6d72f04f6e7eea41855fe808a46/nbformat-4.4.0-py2.py3-none-any.whl)
Collecting pandocfilters>=1.4.1 (from nbconvert->jupyter)
Collecting pygments (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/02/ee/b6e02dc6529e82b75bb06823ff7d005b141037cb1416b10c6f00fc419dca/Pygments-2.2.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/02/ee/b6e02dc6529e82b75bb06823ff7d005b141037cb1416b10c6f00fc419dca/Pygments-2.2.0-py2.py3-none-any.whl)
Collecting testpath (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/15/19/d7bc380c479a184e4a5a9ce516e4e2a773165f89b445f7cdced83d94de25/testpath-0.3.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/15/19/d7bc380c479a184e4a5a9ce516e4e2a773165f89b445f7cdced83d94de25/testpath-0.3.1-py2.py3-none-any.whl)
Collecting defusedxml (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/87/1c/17f3e3935a913dfe2a5ca85fa5ccbef366bfd82eb318b1f75dadbf0affca/defusedxml-0.5.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/87/1c/17f3e3935a913dfe2a5ca85fa5ccbef366bfd82eb318b1f75dadbf0affca/defusedxml-0.5.0-py2.py3-none-any.whl)
Collecting traitlets>=4.2 (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/93/d6/abcb22de61d78e2fc3959c964628a5771e47e7cc60d53e9342e21ed6cc9a/traitlets-4.3.2-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/93/d6/abcb22de61d78e2fc3959c964628a5771e47e7cc60d53e9342e21ed6cc9a/traitlets-4.3.2-py2.py3-none-any.whl)
Collecting mistune>=0.8.1 (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/c8/8c/87f4d359438ba0321a2ae91936030110bfcc62fef752656321a72b8c1af9/mistune-0.8.3-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/c8/8c/87f4d359438ba0321a2ae91936030110bfcc62fef752656321a72b8c1af9/mistune-0.8.3-py2.py3-none-any.whl)
Collecting bleach (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/94/aa/0f7ce53f8688bb9f80c0cffacc3964ddfe08321c509c0bfe5062848951f9/bleach-2.1.4-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/94/aa/0f7ce53f8688bb9f80c0cffacc3964ddfe08321c509c0bfe5062848951f9/bleach-2.1.4-py2.py3-none-any.whl)
Collecting entrypoints>=0.2.2 (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/cc/8b/4eefa9b47f1910b3d2081da67726b066e379b04ca897acfe9f92bac56147/entrypoints-0.2.3-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/cc/8b/4eefa9b47f1910b3d2081da67726b066e379b04ca897acfe9f92bac56147/entrypoints-0.2.3-py2.py3-none-any.whl)
Collecting jupyter-core (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/1d/44/065d2d7bae7bebc06f1dd70d23c36da8c50c0f08b4236716743d706762a8/jupyter_core-4.4.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/1d/44/065d2d7bae7bebc06f1dd70d23c36da8c50c0f08b4236716743d706762a8/jupyter_core-4.4.0-py2.py3-none-any.whl)
Collecting jinja2 (from nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/7f/ff/ae64bacdfc95f27a016a7bed8e8686763ba4d277a78ca76f32659220a731/Jinja2-2.10-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/7f/ff/ae64bacdfc95f27a016a7bed8e8686763ba4d277a78ca76f32659220a731/Jinja2-2.10-py2.py3-none-any.whl)
Collecting jupyter-client (from jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/94/dd/fe6c4d683b09eb05342bd2816b7779663f71762b4fa9c2d5203d35d17354/jupyter_client-5.2.3-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/94/dd/fe6c4d683b09eb05342bd2816b7779663f71762b4fa9c2d5203d35d17354/jupyter_client-5.2.3-py2.py3-none-any.whl)
Collecting prompt-toolkit<2.0.0,>=1.0.0 (from jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/04/d1/c6616dd03701e7e2073f06d5c3b41b012256e42b72561f16a7bd86dd7b43/prompt_toolkit-1.0.15-py3-none-any.whl](https://files.pythonhosted.org/packages/04/d1/c6616dd03701e7e2073f06d5c3b41b012256e42b72561f16a7bd86dd7b43/prompt_toolkit-1.0.15-py3-none-any.whl)
Collecting ipython (from jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/f7/62/2fef7db3a7b75e8099c3d9db2630ae5ba0b9eefefd91f7497862393d90e8/ipython-6.5.0-py3-none-any.whl](https://files.pythonhosted.org/packages/f7/62/2fef7db3a7b75e8099c3d9db2630ae5ba0b9eefefd91f7497862393d90e8/ipython-6.5.0-py3-none-any.whl)
Collecting ipython-genutils (from qtconsole->jupyter)
  Using cached [https://files.pythonhosted.org/packages/fa/bc/9bd3b5c2b4774d5f33b2d544f1460be9df7df2fe42f352135381c347c69a/ipython_genutils-0.2.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/fa/bc/9bd3b5c2b4774d5f33b2d544f1460be9df7df2fe42f352135381c347c69a/ipython_genutils-0.2.0-py2.py3-none-any.whl)
Collecting tornado>=4.0 (from ipykernel->jupyter)
Collecting Send2Trash (from notebook->jupyter)
  Using cached [https://files.pythonhosted.org/packages/49/46/c3dc27481d1cc57b9385aff41c474ceb7714f7935b1247194adae45db714/Send2Trash-1.5.0-py3-none-any.whl](https://files.pythonhosted.org/packages/49/46/c3dc27481d1cc57b9385aff41c474ceb7714f7935b1247194adae45db714/Send2Trash-1.5.0-py3-none-any.whl)
Collecting prometheus-client (from notebook->jupyter)
Collecting pyzmq>=17 (from notebook->jupyter)
  Using cached [https://files.pythonhosted.org/packages/9a/f9/6d7d3d1c83159997e2e7bc74d11e84a83aa1e7f85e6f028341414e7c2141/pyzmq-17.1.2-cp35-cp35m-manylinux1_x86_64.whl](https://files.pythonhosted.org/packages/9a/f9/6d7d3d1c83159997e2e7bc74d11e84a83aa1e7f85e6f028341414e7c2141/pyzmq-17.1.2-cp35-cp35m-manylinux1_x86_64.whl)
Collecting terminado>=0.8.1 (from notebook->jupyter)
  Using cached [https://files.pythonhosted.org/packages/2e/20/a26211a24425923d46e1213b376a6ee60dc30bcdf1b0c345e2c3769deb1c/terminado-0.8.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/2e/20/a26211a24425923d46e1213b376a6ee60dc30bcdf1b0c345e2c3769deb1c/terminado-0.8.1-py2.py3-none-any.whl)
Collecting widgetsnbextension~=3.4.0 (from ipywidgets->jupyter)
  Using cached [https://files.pythonhosted.org/packages/3c/9a/9a690e18e335fc4470a2fa38163774940159375798ba6cce043d5cd94bae/widgetsnbextension-3.4.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/3c/9a/9a690e18e335fc4470a2fa38163774940159375798ba6cce043d5cd94bae/widgetsnbextension-3.4.1-py2.py3-none-any.whl)
Collecting jsonschema!=2.5.0,>=2.4 (from nbformat>=4.4->nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/77/de/47e35a97b2b05c2fadbec67d44cfcdcd09b8086951b331d82de90d2912da/jsonschema-2.6.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/77/de/47e35a97b2b05c2fadbec67d44cfcdcd09b8086951b331d82de90d2912da/jsonschema-2.6.0-py2.py3-none-any.whl)
Collecting six (from traitlets>=4.2->nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/67/4b/141a581104b1f6397bfa78ac9d43d8ad29a7ca43ea90a2d863fe3056e86a/six-1.11.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/67/4b/141a581104b1f6397bfa78ac9d43d8ad29a7ca43ea90a2d863fe3056e86a/six-1.11.0-py2.py3-none-any.whl)
Collecting decorator (from traitlets>=4.2->nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/bc/bb/a24838832ba35baf52f32ab1a49b906b5f82fb7c76b2f6a7e35e140bac30/decorator-4.3.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/bc/bb/a24838832ba35baf52f32ab1a49b906b5f82fb7c76b2f6a7e35e140bac30/decorator-4.3.0-py2.py3-none-any.whl)
Collecting html5lib!=1.0b1,!=1.0b2,!=1.0b3,!=1.0b4,!=1.0b5,!=1.0b6,!=1.0b7,!=1.0b8,>=0.99999999pre (from bleach->nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/a5/62/bbd2be0e7943ec8504b517e62bab011b4946e1258842bc159e5dfde15b96/html5lib-1.0.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/a5/62/bbd2be0e7943ec8504b517e62bab011b4946e1258842bc159e5dfde15b96/html5lib-1.0.1-py2.py3-none-any.whl)
Collecting MarkupSafe>=0.23 (from jinja2->nbconvert->jupyter)
Collecting python-dateutil>=2.1 (from jupyter-client->jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/cf/f5/af2b09c957ace60dcfac112b669c45c8c97e32f94aa8b56da4c6d1682825/python_dateutil-2.7.3-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/cf/f5/af2b09c957ace60dcfac112b669c45c8c97e32f94aa8b56da4c6d1682825/python_dateutil-2.7.3-py2.py3-none-any.whl)
Collecting wcwidth (from prompt-toolkit<2.0.0,>=1.0.0->jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/7e/9f/526a6947247599b084ee5232e4f9190a38f398d7300d866af3ab571a5bfe/wcwidth-0.1.7-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/7e/9f/526a6947247599b084ee5232e4f9190a38f398d7300d866af3ab571a5bfe/wcwidth-0.1.7-py2.py3-none-any.whl)
Collecting backcall (from ipython->jupyter-console->jupyter)
Collecting simplegeneric>0.8 (from ipython->jupyter-console->jupyter)
Collecting setuptools>=18.5 (from ipython->jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/66/e8/570bb5ca88a8bcd2a1db9c6246bb66615750663ffaaeada95b04ffe74e12/setuptools-40.2.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/66/e8/570bb5ca88a8bcd2a1db9c6246bb66615750663ffaaeada95b04ffe74e12/setuptools-40.2.0-py2.py3-none-any.whl)
Collecting pexpect; sys_platform != "win32" (from ipython->jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/89/e6/b5a1de8b0cc4e07ca1b305a4fcc3f9806025c1b651ea302646341222f88b/pexpect-4.6.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/89/e6/b5a1de8b0cc4e07ca1b305a4fcc3f9806025c1b651ea302646341222f88b/pexpect-4.6.0-py2.py3-none-any.whl)
Collecting jedi>=0.10 (from ipython->jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/3d/68/8bbf0ef969095a13ba0d4c77c1945bd86e9811960d052510551d29a2f23b/jedi-0.12.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/3d/68/8bbf0ef969095a13ba0d4c77c1945bd86e9811960d052510551d29a2f23b/jedi-0.12.1-py2.py3-none-any.whl)
Collecting pickleshare (from ipython->jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/9f/17/daa142fc9be6b76f26f24eeeb9a138940671490b91cb5587393f297c8317/pickleshare-0.7.4-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/9f/17/daa142fc9be6b76f26f24eeeb9a138940671490b91cb5587393f297c8317/pickleshare-0.7.4-py2.py3-none-any.whl)
Collecting ptyprocess; os_name != "nt" (from terminado>=0.8.1->notebook->jupyter)
  Using cached [https://files.pythonhosted.org/packages/d1/29/605c2cc68a9992d18dada28206eeada56ea4bd07a239669da41674648b6f/ptyprocess-0.6.0-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/d1/29/605c2cc68a9992d18dada28206eeada56ea4bd07a239669da41674648b6f/ptyprocess-0.6.0-py2.py3-none-any.whl)
Collecting webencodings (from html5lib!=1.0b1,!=1.0b2,!=1.0b3,!=1.0b4,!=1.0b5,!=1.0b6,!=1.0b7,!=1.0b8,>=0.99999999pre->bleach->nbconvert->jupyter)
  Using cached [https://files.pythonhosted.org/packages/f4/24/2a3e3df732393fed8b3ebf2ec078f05546de641fe1b667ee316ec1dcf3b7/webencodings-0.5.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/f4/24/2a3e3df732393fed8b3ebf2ec078f05546de641fe1b667ee316ec1dcf3b7/webencodings-0.5.1-py2.py3-none-any.whl)
Collecting parso>=0.3.0 (from jedi>=0.10->ipython->jupyter-console->jupyter)
  Using cached [https://files.pythonhosted.org/packages/09/51/9c48a46334be50c13d25a3afe55fa05c445699304c5ad32619de953a2305/parso-0.3.1-py2.py3-none-any.whl](https://files.pythonhosted.org/packages/09/51/9c48a46334be50c13d25a3afe55fa05c445699304c5ad32619de953a2305/parso-0.3.1-py2.py3-none-any.whl)
Installing collected packages: six, decorator, ipython-genutils, traitlets, jupyter-core, jsonschema, nbformat, pandocfilters, pygments, testpath, defusedxml, mistune, webencodings, html5lib, bleach, entrypoints, MarkupSafe, jinja2, nbconvert, tornado, python-dateutil, pyzmq, jupyter-client, wcwidth, prompt-toolkit, backcall, simplegeneric, setuptools, ptyprocess, pexpect, parso, jedi, pickleshare, ipython, ipykernel, jupyter-console, qtconsole, Send2Trash, prometheus-client, terminado, notebook, widgetsnbextension, ipywidgets, jupyter
Successfully installed MarkupSafe-1.0 Send2Trash-1.5.0 backcall-0.1.0 bleach-2.1.4 decorator-4.3.0 defusedxml-0.5.0 entrypoints-0.2.3 html5lib-1.0.1 ipykernel-4.8.2 ipython-6.5.0 ipython-genutils-0.2.0 ipywidgets-7.4.0 jedi-0.12.1 jinja2-2.10 jsonschema-2.6.0 jupyter-1.0.0 jupyter-client-5.2.3 jupyter-console-5.2.0 jupyter-core-4.4.0 mistune-0.8.3 nbconvert-5.3.1 nbformat-4.4.0 notebook-5.6.0 pandocfilters-1.4.2 parso-0.3.1 pexpect-4.6.0 pickleshare-0.7.4 prometheus-client-0.3.1 prompt-toolkit-1.0.15 ptyprocess-0.6.0 pygments-2.2.0 python-dateutil-2.7.3 pyzmq-17.1.2 qtconsole-4.4.1 setuptools-40.2.0 simplegeneric-0.8.1 six-1.11.0 terminado-0.8.1 testpath-0.3.1 tornado-5.1 traitlets-4.3.2 wcwidth-0.1.7 webencodings-0.5.1 widgetsnbextension-3.4.1[B]
You are using pip version 8.1.1, however version 18.0 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.[/B][/SIZE][I][B]


i still run the command to open jupyter notebook and it opens fine. however all people who have followed the way to do this worked just fine for them, but when i shut down and restart it doesnt open up by directly typing in 'jupyter notebook' in the terminal.

i tried updating pip3 with the upgrade command that it gave me and then the jupyter refused to install

in one particular forum i was asked to type in python-m pip3 instead of pip3, but the result was the sam

please help me install jupyter notebook
[/B]


[/I]

---

