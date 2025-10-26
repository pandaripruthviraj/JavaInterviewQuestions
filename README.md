# JavaInterviewQuestions
This repository is a collection of basic Java interview questions for quick brush up on your knowledge.

Question 1: What is the difference between HashMap vs HashTable, which one is synchronized?
Question 2: What difference between Hashmap vs concurrent hashmap?
Question 3: How to create a custom immutable class in Java?
A: It’s a classic interview question that will have follow-up questions,

In order to create an immutable class, you should follow the below steps:

Make your class final, so that no other classes can extend it.
Make all your fields final, so that they’re initialized only once inside the constructor and never modified afterward.
Don’t expose setter methods.
When exposing methods that modify the state of the class, you must always return a new instance of the class.
If the class holds a mutable object:
Inside the constructor, make sure to use a clone copy of the passed argument and never set your mutable field to the real instance passed through the constructor, this is to prevent the clients who pass the object from modifying it afterward.
Make sure to always return a clone copy of the field and never return the real object instance.
public final class ImmutableStudent {
    private final int id;
    private final String name;
    public ImmutableStudent(int id, String name) {
        this.name = name;
        this.id = id;
    }
    public int getId() {
        return id;
    }
    public String getName() {
        return name;
    }
}
Question 4: What are the in-built immutable classes in Java?

String
Wrapper classes such as Integer, Long, Double, etc.
Immutable collection classes such as Collections.singletonMap() etc.
java.lang.StackTraceElement
Java enums (ideally they should be)
java.util.Locale
java.util.UUID
Question 5: Difference between Aggregation vs composition?

The main difference between aggregation and composition is that aggregation is an association among two objects that have the “has a” relationship while the composition is a special type of aggregation that describes ownership.


Question 6: How to create an immutable map in Java, that we can’t modify after adding the data?

There are various ways in which we can create an Immutable Map.

– Using Collections.unmodifiableMap()

– Using Map.of()

– Using Map.ofEntries()

– Using Map.copyOf()

Question 7: Explain Throw, throws, and throwable keywords in Java.

Throw: The throw keyword in Java is used to explicitly throw an exception from a method or any block of code.

throw Instance

//Example: throw new ArithmeticException("/ by zero");

Throws: The throws is also a keyword in java that is used in the method signature to indicate that this method may throw mentioned exceptions. The caller to such methods must handle the mentioned exceptions either using try-catch blocks or using the throws keyword.

Java. lang.Throwable Class: Throwable is a superclass for all types of errors and exceptions in java. This class is a member of java.lang package. Only instances of this class or its subclasses are thrown by the java virtual machine or by the throw statement. The only argument of catch block must be of this type or its subclasses. If you want to create your own customized exceptions, then your class must extend this class.

Question 8: Explain the Diamond problem in Java and how to solve that.

In Java, the diamond problem is related to multiple inheritances.

Remember that Java does not support multiple inheritances because of the diamond problem. This is the problem,

interface Interface1 {
    default public void foo() { System.out.println("Interface1's foo"); }
}
interface Interface2 {
    default public void foo() { System.out.println("Interface2's foo"); }
}
public class Diamond implements Interface1, Interface2 {
    public static void main(String []args) {
        new Diamond().foo();
    }
}
Error:(9, 8) java: class Diamond inherits unrelated defaults for foo() from types Interface1 and Interface2

In this case, resolve the conflict manually by overriding foo function in Diamond class and using the super keyword to explicitly mention which method definition to use:

public void foo() { Interface1.super.foo(); }
Question 9: Java 8 Interface changes?

from Java 8, we can have default methods, functional interfaces, and static methods in the interfaces

Question 10: How to create an Object in Java? Explain Different ways to do it.

Consider a class Tester which has implemented Cloneable interface. Now you can initialize an object using following five ways:

1. Using new keyword.

Tester tester1 = new Tester();
2. Using Class.forName() method

Tester tester2 = (Tester)Class.forName("Tester").newInstance();
3. Using clone method.

Tester tester3 = tester1.clone();
4. Using Constructor.forName() method

Tester tester4 = Tester.class.getConstructor().newInstance();
5. Using Deserialization

ObjectInputStream objectInputStream = new ObjectInputStream(inputStream );
Tester tester5 = (MyObject) objectInputStream.readObject();
