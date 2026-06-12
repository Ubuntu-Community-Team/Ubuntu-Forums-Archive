---
title: "Rails: Upload problem"
date: 2006-12-08
forum: Programming Talk
---

### Post by Blacktalon on 2006-12-08
Hello everyone,
Sad to say I am having another problem with RoR, I am currently trying to get my upload file to work.  But the only way I know how to do this is with <% form_tag :action => 'upload', :multipart => true %>, this works nice.  But the stuff I need to do with my upload page won't work with this style so I need to use the form_remote_tag, but the problem is that the form_remote_tag doesn't like :multipart.  And I need that in order for my controller to use the .orginal_filename function.  I read that inside the :html {.....} of form_remote_tag I can put something simile to the :multipart, which is :enctype => 'multipart/form-data' , but again it doesn't work.

Does anyone have any idea's?
 

Here's my code in case you want to get an idea on what I am doing:<%= link_to_function 'Show/Hide Upload passwords form', "Effect.toggle('uploadPwForm', 'blind') ;" %>

<%= form_remote_tag :html => {:id => "uploadPwForm", :style => 'display: none;', :enctype => 'multipart/form-data'},
                    :url => {:action => 'upload_passwords', :form_id => 'uploadPwForm'},
                    :loading => "Element.show('loading')",
                    :complete => "Element.hide('loading')"
                     %>

<p><label for="password_entity_id">Entity</label>
<%= select : password, :entity_id, projectEntity.find(:all).collect {|e| [ e.name, e.id ] }, {: prompt => 'Choose one...'} %>

<p><label for="password_max_completes">Maximum Number of Completes</label>
<%= text_field : password, :max_completes, :size => 6, :value => 1 %></p>
<p><label for="password_file">Password File</label>
<%= file_field 'password', 'data' %></p>
<%= submit_tag "Upload Passwords" %>
  
<br /><br />
<%= link_to_function 'Close', "Effect.BlindUp('uploadPwForm');" %>  
<br /><br />
<%= end_form_tag %>

__________________________________________________

---

### Post by Blacktalon on 2006-12-08
and for the controller section of this:

username = params[: password][:username] || nil
    max_completes = params[: password][:max_completes].to_i || 1
    entity_id = params[: password][:entity_id].to_i
    puts params[: password][:data]
    upload_password = params[: password][:data].to_a || nil
    
    entity_id = nil if entity_id == 0
    
    @upload = projectPassword.new    
    passwords = ()
    password_array = Array.new
    
    passwords = projectPassword.find(:all)
    
    # Improve performance by converting list of current passwords into a set rather than an array.
    # This is because we are heavily using the include? method.  include? for an array is linear,
    # whereas include? for a set is constant  
    passwords = passwords.to_set  
    if request.post?
            path = "/files/" + params[: password][:data].original_filename
            root = "#{RAILS_ROOT}/public" 
            data = params[: password][:data].read
            @upload.upload(data, root+path)
     # upload_password << [@upload]
      upload_password.each do |password_row|
        password_row_array  = password_row.split
        username = password_row_array[0]
        password = password_row_array[1]
        if passwords.include? password
          flash[:error] = "Password already exists"
        else
          password_array << [username, password, entity_id, max_completes]    
        end
      end
   end
end
__________________________________________________

---

### Post by Blacktalon on 2006-12-08
Never Mind, I just got struck with some intellegence.  And re did my rhtml code to this and it looks cooler now:

<%= link_to_function 'Show/Hide Upload passwords form', show_element('new_upload') %>
<div id="new_upload" class ="window_form" style="display:none">
  <div id="new_upload_title" class="title_bar">
    New Upload
    <%= #hide_element('new_survey')
     %>
    <!--<div id="new_survey_close_button", onclick="" style="border:2px; height:5px; width:5px;">-->
    
    <!--</div>-->
    <%= link_to_function '<img src="/images/close.jpg" style="float:right; border:0px; display:inline;"  />', hide_element('new_upload') %>
  </div>

<%= form_tag :html => {:id => 'new_upload_form'}, :multipart => true,
                    :url => {:action => 'upload_passwords'},
                    :loading => "Element.show('loading')",
                    :complete => "Element.hide('loading')" %>
<p><label for="password_entity_id">Entity</label>
<%= select : password, :entity_id, projectEntity.find(:all).collect {|e| [ e.name, e.id ] }, {: prompt => 'Choose one...'} %>

<p><label for="password_max_completes">Maximum Number of Completes</label>
<%= text_field : password, :max_completes, :size => 6, :value => 1 %></p>
<p><label for="password_file">Password File</label>
<%= file_field 'password', 'data' %></p>
  <%= submit_tag "Upload Passwords" %>
<%= end_form_tag %>

</div>
<%= draggable_element('new_upload', :handle => "'new_upload_title'")%>

---

