---
title: "Firefox doesn,t display parse error"
date: 2010-07-17
forum: Programming Talk
---

### Post by fluteofliar on 2010-07-17
Hi,all of you
i were trying to run php script but every time i suffered through one common problem
that when i did some error in php script it doesn,t display a error or any warning message on
firefox(which i am using as browser) rather than showing a blank screen .My php.ini file configuration is as follow
engine = On
short_open_tag = On
precision = 14
y2k_compliance = On
output_buffering = 4096
zlib.output_compression = Off
implicit_flush = Off
unserialize_callback_func =
serialize_precision = 100
allow_call_time_pass_reference = Off
safe_mode = Off
safe_mode_gid = Off
safe_mode_include_dir =
safe_mode_exec_dir =
safe_mode_allowed_env_vars = PHP_
safe_mode_protected_env_vars = LD_LIBRARY_PATH
;open_basedir =     //its commented with semicolon
disable_functions =
disable_classes =
expose_php = On
max_execution_time = 30
max_input_time = 60
;max_input_nesting_level = 64  //its commented with semicolon
memory_limit = -1
error_reporting = E_ALL & ~E_NOTICE
display_errors = On
display_startup_errors = Off
log_errors = Onlog_errors_max_len = 1024
ignore_repeated_errors = Off
ignore_repeated_source = Off
report_memleaks = On
track_errors = Off
html_errors = On
variables_order = "GPCS"
request_order = "GP"
register_globals = Off
register_long_arrays = Off
register_argc_argv = Off
auto_globals_jit = On
post_max_size = 32M
magic_quotes_gpc = Off
magic_quotes_runtime = Off
magic_quotes_sybase = Off
auto_append_file =
default_mimetype = "text/html"
doc_root =
; The directory under which PHP opens the script using /~username used only
; if nonempty.
; [http://php.net/user-dir](http://php.net/user-dir)
user_dir =
; extension_dir = "./"
; extension_dir = "ext"
enable_dl = Off
file_uploads = On
;upload_tmp_dir =
upload_max_filesize = 2M
max_file_uploads = 20
allow_url_fopen = On
allow_url_include = Off
defpdo_mysql.cache_size = 2000
ault_socket_timeout = 60
pdo_mysql.default_socket=define_syslog_variables  = Off
SMTP = localhost
smtp_port = 25

---

### Post by cariboo on 2010-07-18
A bump for the move.

---

