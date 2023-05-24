# django-crud

## Install virtual environment
python -m venv myworld

## Activate the environment
source myworld/bin/activate
--> (myworld) ... $

## Install Django
(myworld) ... $ python -m pip install Django

## Check Django version
(myworld) ... $ django-admin --version

## Create Django project
django-admin startproject my_tennis_club

## Run project
cd my_tennis_club
python manage.py runserver

## Create App
python manage.py startapp members
1. Add App to src/settings.py INSTALLED_APPS[]
2. Create urls.py file
3. Edit src/urls.py to add App (ex: path('', include('members.urls')))
4. Create templates folder and add html files
5. Edit views.py to render html files

## Create Table (Model)
1. Open models.py file in App
2. Add a Member table by creating a Member class
3. Migrate db: python manage.py makemigrations members && python manage.py migrate

## Open shell
python manage.py shell
>>> from members.models import Member
>>> Member.objects.all()
>>> member = Member(firstname='Emil', lastname='Refsnes')
>>> member.save()
>>> Member.objects.all().values()
>>> member1 = Member(firstname='Tobias', lastname='Refsnes')
>>> member2 = Member(firstname='Linus', lastname='Refsnes')
>>> member3 = Member(firstname='Lene', lastname='Refsnes')
>>> member4 = Member(firstname='Stale', lastname='Refsnes')
>>> member5 = Member(firstname='Jane', lastname='Doe')
>>> members_list = [member1, member2, member3, member4, member5]
>>> for x in members_list:
>>>   x.save()
update
>>> from members.models import Member
>>> x = Member.objects.all()[4]
>>> x.firstname
>>> x.firstname = "Stalikken"
>>> x.save()
delete
>>> from members.models import Member
>>> x = Member.objects.all()[5]
>>> x.firstname
>>> x.delete()

## Create User
python manage.py createsuperuser

## Include Model in the Admin Interface
members/admin.py
admin.site.register(Member, MemberAdmin)