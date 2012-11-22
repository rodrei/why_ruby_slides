# Why Ruby?

!SLIDE

# Why Ruby?

## by Rodrigo Pavano

!SLIDE

# Why this talk?

!SLIDE left

# Matz: It's impossible to design a perfect language

!SLIDE

# Two ways to look at a language

## What can be done with it?
## How does the user feel using it?

!SLIDE

# Ruby focuses on the HOW and not so much on the WHAT

!SLIDE

# Ruby focuses on PEOPLE and not on MACHINES


!SLIDE dark

# Ruby principles

* Uniform access principle
* Everything is an expression
* Correspondance principle  
* No special contexts

!SLIDE left

# Uniform Access Principle

All services offered by a module should be available through a uniform
notation, which does not betray whether they are implemented through
storage or through computation

Bertrand Meyer

!SLIDE

# Attributes and methods should be accessed the same way

!SLIDE code

```ruby
person.name
person.name=
```

!SLIDE code

```ruby
hash[i] == hash.[](i)
```

!SLIDE code
```ruby
hash[i]= value ==  hash.[]=(i, value)
```

!SLIDE 

# Ruby's rules

## Everything is an object

## Objects expose methods and only methods

!SLIDE

# There are no primitives, everything is an object

### 100, true, false, nil

!SLIDE Dark

# Everything is an expression

!SLIDE

## hash.keys

!SLIDE

## x = hash.keys

!SLIDE

# 3 Types

### 1- Assignment expressions
### 2- Control flow expressions
### 3- Method call expressions

!SLIDE

# 1- Assignments

## name = "hello"

!SLIDE

# 2- Control Flow

```ruby 
  if @alive
    true
  end
```

!SLIDE

# && and || are not methods, they are control structures

!SLIDE

## person.group && person.group.name

!SLIDE

## name = person.name || "unknown"

!SLIDE

# 3- Method Call

## person.name

!SLIDE

## Nesting expressions

```ruby
if foo
  x = 1
else
  x = 2
end
```

!SLIDE

## Nesting expressions

```ruby
x = if foo
      1
    else
      2
    end
```

!SLIDE

## Grouping all kinds

```ruby
if person = group.person
  person.save
end
```

!SLIDE dark

# Correspondance Principle

!SLIDE

## expr
## should be semanticaly equal to
## lambda { expre }

!SLIDE 

# Why it is important

```ruby
person.some_mutation
```

!SLIDE

# Why it is important

```ruby
mutex.syncronize {
  person.some_mutation
}
```

!SLIDE

```ruby
common_before
expression A
common_after

common_before
expression B
common_after
```

!SLIDE

```ruby
common { expression A }
common { expression B }
```

!SLIDE

## Violations of this principle appear as unexpected failures, irregularities and restrictions

!SLIDE
## Javascript violates this principle

### this
### is not semantically equal than
### lambda { this }

!SLIDE

## Javascript violates this principle

### return
### is not semantically equal than
### lambda { return }

!SLIDE

## This problem exists because there is only one type of callable

```ruby
lambda {
  lambda {
    lambda {
      return;
    }
  }
}
```

!SLIDE
## Solution

```ruby
  method {
    lambda {
      lambda {
        return;
      }
    }
  }
```

!SLIDE

## Ruby: Method vs Proc

### Method => Scope for return, yield, super
### proc   => function to satisty the correspondance principle

!SLIDE
## why lambda?

### Anonymous method that inherits local variables
### scope for return yield and super

!SLIDE

# No special contexts

!SLIDE

## Every ruby program is a tree of expressions

## Every expression has an associated self


!SLIDE code

```ruby
class Person
  puts self #=> Person

    def hello
      puts self #=> <Person:sldjfkasd>
    end
end

Person.new.hello
```

!SLIDE
### This is useful to define things that might appear as language extensions

### attr_accessor
### validates_presence_of




