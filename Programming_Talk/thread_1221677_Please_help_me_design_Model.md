---
title: "Please help me design Model"
date: 2009-07-24
forum: Programming Talk
---

### Post by urosh2 on 2009-07-24
Hi.

I want to create phone book. I want that this phone book list will be
ordered by number of dialing this number. I think of using two tables
one with phone numbers and one for phone dialing statistics (how many
times user dialed number). Each user has his own ordering rule based
on his user-name. I will populate this phonebook statistics with other
function regular running.

This is what I have so far.

class phonebook(models.Model):
        person_company = models.CharField(blank=True,max_length=30)
        address = models.CharField(blank=True,max_length=50)
        e_mail = models.EmailField(blank=True,max_length=70)
        number = models.CharField(unique=True,max_length=15)
        dialed = models.ForeignKey('phonebook_stat')
        def __unicode__(self):
                return self.person_company

class phonebook_stat(models.Model):
        username = models.CharField(max_length=30)
        number = models.CharField(max_length=15)
        dialed_times = models.IntegerField(max_length=10)
        class Admin:
                pass
in admin.py
class PhonebookAdmin(admin.ModelAdmin):
        def queryset(self, request):
                qs = super(PhonebookAdmin, self).queryset(request)
                global caller_id
                caller_id = str(request.user)
                return qs
        list_per_page = 20
        search_fields = ('person_company','number')
        list_display = ['person_company','number','address',]
        fields = ('person_company','number','address','e_mail',)
        #ordering = (order_common_used,)

THANK YOU in advance.

---

