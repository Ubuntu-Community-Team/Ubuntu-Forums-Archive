---
title: "help decode wxruby error?"
date: 2010-07-02
forum: Programming Talk
---

### Post by unter on 2010-07-02
sorry i have much inability and frustrate trying to understand what is here.

i follow this instruction [http://rubyonwindows.blogspot.com/2007/11/getting-started-with-wxruby-gui-toolkit.html](http://rubyonwindows.blogspot.com/2007/11/getting-started-with-wxruby-gui-toolkit.html)

to run this code

```
require 'rubygems'
require 'wx'

class MyFrame < Frame
  def initialize()
        super(nil, -1, 'My Frame Title')
        # First create the controls
        @my_panel = Panel.new(self)
        @my_label = StaticText.new(@my_panel, -1, 'My Label Text', DEFAULT_POSITION, DEFAULT_SIZE, ALIGN_CENTER)
        @my_textbox = TextCtrl.new(@my_panel, -1, 'Default Textbox Value')
        @my_combo = ComboBox.new(@my_panel, -1, 'Default Combo Text', DEFAULT_POSITION, DEFAULT_SIZE, ['Item 1', 'Item 2', 'Item 3'])
        @my_button = Button.new(@my_panel, -1, 'My Button Text')
        # Bind controls to functions
        evt_button(@my_button.get_id()) { |event| my_button_click(event)}
        # Now do the layout
        @my_panel_sizer = BoxSizer.new(VERTICAL)
        @my_panel.set_sizer(@my_panel_sizer)
        @my_panel_sizer.add(@my_label, 0, GROW|ALL, 2)
        @my_panel_sizer.add(@my_textbox, 0, GROW|ALL, 2)
        @my_panel_sizer.add(@my_combo, 0, GROW|ALL, 2)
        @my_panel_sizer.add(@my_button, 0, GROW|ALL, 2)        
        show()
    end

    def my_button_click(event)
        # Your code here
    end

end

class MyApp < App
  def on_init
    MyFrame.new
  end
end

MyApp.new.main_loop()

```

for erros:

```


#ruby testcode.rb 
/var/lib/gems/1.8/gems/wxruby-2.0.1-x86-linux/lib/wxruby2.so: /var/lib/gems/1.8/gems/wxruby-2.0.1-x86-linux/lib/wxruby2.so: symbol _ZN13wxAuiNotebook14ShowWindowMenuEv, version WXU_2.8.5 not defined in file libwx_gtk2u_aui-2.8.so.0 with link time reference - /var/lib/gems/1.8/gems/wxruby-2.0.1-x86-linux/lib/wxruby2.so (LoadError)
    from /usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /var/lib/gems/1.8/gems/wxruby-2.0.1-x86-linux/lib/wx.rb:12
    from /usr/lib/ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require'
    from /usr/lib/ruby/1.8/rubygems/custom_require.rb:36:in `require'
    from testcode.rb:
```$ 

:cry:

---

### Post by unter on 2010-07-02
still is battling with this error. i just try to execute on of built in wxruby samples but is error

```
# ruby -rubygems minimal.rb 
/var/lib/gems/1.8/gems/wxruby-2.0.1-x86-linux/lib/wxruby2.so: /var/lib/gems/1.8/gems/wxruby-2.0.1-x86-linux/lib/wxruby2.so: symbol _ZN13wxAuiNotebook14ShowWindowMenuEv, version WXU_2.8.5 not defined in file libwx_gtk2u_aui-2.8.so.0 with link time reference - /var/lib/gems/1.8/gems/wxruby-2.0.1-x86-linux/lib/wxruby2.so (LoadError)
    from /usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /var/lib/gems/1.8/gems/wxruby-2.0.1-x86-linux/lib/wx.rb:12
    from /usr/lib/ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require'
    from /usr/lib/ruby/1.8/rubygems/custom_require.rb:36:in `require'
    from minimal.rb:8
```

---

