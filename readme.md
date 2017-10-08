# C++ coding style

This for my personal coding style guide for my c++ projects based on Google c++ [guide](https://google.github.io/styleguide/cppguide.html).

# Formatting

## Line length

Each line of text in the code should not exceed 80 characters including comments followed by the code.

Exceptions: 
1. File directories
2. Url links
3. Header guards

## Characters

Most of the code should be written in ASCII characters; however, any character which is in UTF-8 charset is acceptable.

Prohibited: 
1. c++11 char16, char32_t character types (as they are not UTF-8 charset)
2. wchar_t (unless developing for WIN32API)

## No tabs, but spaces

Indentation should be in 2 spaces each. NO TABS.

## Function Declarations and Definitions

If they fit, function return type, name, parameters should be written on the same line.

If they does not fit, then appropriate line breaks should be used for line readability.

Examples:  
```c++
ReturnType ClassName::FunctionName(Type par_name1, Type par_name2) {
  DoSomething();
  ...
}
``` 
```c++
ReturnType ClassName::ReallyLongFunctionName(Type par_name1, Type par_name2,
                                             Type par_name3) {
  DoSomething();
  ...
}
```
```c++
ReturnType LongClassName::ReallyReallyReallyLongFunctionName(
    Type par_name1,  // 4 space indent
    Type par_name2,
    Type par_name3) {
  DoSomething();  // 2 space indent
  ...
}
```

Some points to note:  
1. Choose good parameter names (will be discussed in naming rules)
2. Parameter names should never be omitted
3. The open curly brace is always on the end of the last line of the function declaration, not the start of the next line.
4. The close curly brace is either on the last line by itself or on the same line as the open curly brace.
5. There should be a space between the close parenthesis and the open curly brace.
6. All parameters should be aligned if possible.
7. Wrapped parameters have a 4 space indent.

## Function calls

Similar to function definitions.

Examples:
```c++
bool result = DoSomething(argument1, argument2, argument3);
```
```c++
bool result = DoSomething(averyveryveryverylongargument1,
                          argument2, argument3);
```
```c++
if (...) {
  ...
  ...
  if (...) {
    bool result = DoSomething(
        argument1, argument2,  // 4 space indent
        argument3, argument4);
    ...
  }
```

Note: also try to create variables which can shorten the parameter names

## Conditionals

1. No space inside parenthesis.
2. `else` statement goes on the same line as the closing brace
3. There should be braces for all if statements (no omittance even if it is a single line statement)


## Loops and Switch statements 

1. Braces are not optional
2. `case` should not have curly brackets
3. For `switch`, there should always be a `default` case.

## Pointer and Reference Expressions

1. No spaces between period or arrow. 
2. `* &` should be in front of the type not variable names.
3. no multiple declaration for pointers and references.

## Boolean Expressions

`&& ||` should be start of the line when the line is exceeding the 80 limit.

## Return values

No parenthesis on return values.

## Variable and Array initialization

Parenthesis are used when: 
1. Copying variable 
2. User-defined class

Other than those two usage, `=` is used.

## Preprocessor directives 

This should start at the start of line regardless of code.

## Class Format 

`public`, `protected`, and `private` order and each indented one space.

Member variables comes first; member functions comes after the variable declaration.

Functions and Variables are grouped into their similarities.

`isFunctionName()` is for Boolean member functions (predicate).  
`getVariableName()` is Get function for `Variable` in class.  
`setVariableName()` is Set function for `Variable` in class.

## Constructor Initializer Lists.

Preferably one line, but it can be over multiple lines

Examples: 
```c++
// When everything fits on one line:
MyClass::MyClass(int var) : some_var_(var) {
  DoSomething();
}

// If the signature and initializer list are not all on one line,
// you must wrap before the colon and indent 4 spaces:
MyClass::MyClass(int var)
    : some_var_(var), some_other_var_(var + 1) {
  DoSomething();
}

// When the list spans multiple lines, put each member on its own line
// and align them:
MyClass::MyClass(int var)
    : some_var_(var),             // 4 space indent
      some_other_var_(var + 1) {  // lined up
  DoSomething();
}

// As with any other code block, the close curly can be on the same
// line as the open curly, if it fits.
MyClass::MyClass(int var)
    : some_var_(var) {}
```

## Namespace Formatting

No indents for the contents of namespaces


# Naming 

## General Naming 

Names should be descriptive; and constant for call codes.

Use lowercase and underscores for general naming.

## File Names

Should be in lowercase and underscores or dashes

## Type Names

Use CamelCase for Type names. No underscores.

## Variable Names

### Common Variable names

Examples:  
```c++
string table_name;  // OK - uses underscore.
string tablename;   // OK - all lowercase.
```

### Class Data Members

Same as common variable names, but there is a trailing underscore in the end.

### Struct Members

Same as common variable names

## Constant Names 

Named in CamelCase notation and starts in `k`. 

## Function Names

Follows CamelCase rule. No underscores. 

For `get`, `set`, and `is` functions for classes, the first letter is not capitalized. 



# Updates

Oct. 8, 2017: Initial creation based on Google c++ guide. 

