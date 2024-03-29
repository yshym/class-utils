### Utils for simplifying work with classes

#### Usage:

`pip install class-utils`

---

<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->

#### Properties:
1. [default_property](#default_property)
2. [default_getter](#default_getter)
3. [typed_property](#typed_property)

#### Mixins:
1. [DefaultRepresentationMixin](#defaultrepresentationmixin)

<!-- markdown-toc end -->



---

#### default_property

``` python
from class_utils import default_property


class Point():
    x = default_property('x')
    y = default_property('y')

    def __init__(self, x, y):
        self.x = x
        self.y = y


point1 = Point(1, 4)

print(point1.x) # => 1

point1.x = 3
print(point1.x) # => 3
```

---

#### default_getter

``` python
from class_utils import default_getter


class Point():
    x = default_getter('x')
    y = default_getter('y')

    def __init__(self, x, y):
        self._x = x
        self._y = y


point1 = Point(1, 4)

print(point1.x) # => 1
```

---

#### typed_property

``` python
from class_utils import typed_property


class Person():
    name = typed_property('name', str)

    def __init__(self, name):
        self.name = name


person1 = Person('Bill')
print(person1.name) # => 'Bill'

person1.name = 123 # => TypeError: name must be a <class 'str'>
```

---

#### DefaultRepresentationMixin

``` python
from class_utils import default_property, DefaultRepresentationMixin


class Date(DefaultRepresentationMixin):
    day = default_property('day')
    month = default_property('month')
    year = default_property('year')

    def __init__(self, day, month, year):
        self.day = day
        self.month = month
        self.year = year


date1 = Date(12, 12, 2012)
print(date1) # => Date({'_day': 12, '_month': 12, '_year': 2012})
```
