# Lab-8_202001039


## Name: Vishrut Shah
## ID: 202001039

# Lab Exercises
import org.junit.Test;  
import static org.junit.Assert.*;  

public class BoaTest {
   
    @Test
    public void testIsHealthy() {
        Boa boa1 = new Boa("Sneaky", 6, "granola bars");
        assertTrue(boa1.isHealthy());
       
        Boa boa2 = new Boa("Slithery", 8, "pizza");
        assertFalse(boa2.isHealthy());
    }
   
    @Test
    public void testFitsInCage() {
        Boa boa1 = new Boa("Slinky", 4, "mice");
        assertTrue(boa1.fitsInCage(5));
        assertFalse(boa1.fitsInCage(3));
       
        Boa boa2 = new Boa("Curly", 10, "rabbits");
        assertTrue(boa2.fitsInCage(12));
        assertFalse(boa2.fitsInCage(9));
    }
}  


The code includes two test cases for the Boa class.

In the first test case, the isHealthy method is being tested. Two Boa objects are created with distinct favorite foods, and it is verified that isHealthy returns true for the first object and false for the second object.

The second test case is for the fitsInCage method. Two Boa objects with different lengths are created, and their ability to fit in cages of different lengths is tested. The first boa is expected to fit in a cage of length 5 but not 3, while the second boa is expected to fit in a cage of length 12 but not 9.


import org.junit.Before;  
import org.junit.Test;  
import static org.junit.Assert.*;  

public class BoaTest {
   
    private Boa jen;
    private Boa ken;
   
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
   
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
   
    @Test
    public void testFitsInCage() {
        assertTrue(jen.fitsInCage(3));
        assertFalse(ken.fitsInCage(2));
    }
}  

In the BoaTest class, we have created two private fields named "jen" and "ken". These fields are initialized with Boa objects inside the setUp method. We have also made modifications to the testIsHealthy and testFitsInCage methods to use these Boa objects for testing.

It is important to note that the setUp method will be executed before each test method. Therefore, any changes made to the "jen" and "ken" objects during a test will not impact the objects used in other tests. This ensures that each test is run independently and does not affect the outcome of other tests.

import org.junit.Before;  
import org.junit.Test;  
import static org.junit.Assert.*;  

public class BoaTest {
   
    private Boa jen;
    private Boa ken;
   
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
   
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
   
    @Test
    public void testFitsInCage() {
        assertTrue(jen.fitsInCage(3));
        assertFalse(ken.fitsInCage(2));
    }
}  
In this code example, we included additional assertions in the testIsHealthy and testFitsInCage methods to validate the behavior of the Boa class. The assertions in the testIsHealthy method verify that both Boa objects are healthy and return true when the isHealthy method is called. The assertions in the testFitsInCage method validate that the fitsInCage method returns the expected results for both Boa objects, depending on the length of the cage. By including these assertions, we increase the confidence in the correctness of the Boa class, and the test suite is now more comprehensive.

import org.junit.Before;  
import org.junit.Test;  
import static org.junit.Assert.*;  

public class BoaTest {
   
    private Boa jen;
    private Boa ken;
   
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
   
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
   
    @Test
    public void testFitsInCage() {
        assertFalse(jen.fitsInCage(1)); // cage length less than boa length
        assertTrue(jen.fitsInCage(2)); // cage length equal to boa length
        assertTrue(jen.fitsInCage(3)); // cage length greater than boa length
       
        assertFalse(ken.fitsInCage(2)); // cage length less than boa length
        assertTrue(ken.fitsInCage(3)); // cage length equal to boa length
        assertTrue(ken.fitsInCage(4)); // cage length greater than boa length
    }
}  
In this example, we improved the testFitsInCage method by adding multiple assertions to verify that the fitsInCage method returns the expected results for different scenarios involving jen and ken. Specifically, we checked whether jen and ken fit in cages that are shorter, equal, or longer than their length.

By doing this, we made the testFitsInCage method more thorough and able to catch potential bugs in the fitsInCage method for different input values. This will help ensure the reliability of the method and the overall quality of the code.


public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;

    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }

    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }

    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }

    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}  


Here is the updated code for the BoaTest class with the new testLengthInInches() method:

import static org.junit.Assert.*;  
import org.junit.Before;  
import org.junit.Test;  

public class BoaTest {
    private Boa jen;
    private Boa ken;

    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }

    @Test
    public void testIsHealthy() {
        assertFalse(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }

    @Test
    public void testFitsInCage() {
        assertTrue(jen.fitsInCage(24));
        assertFalse(jen.fitsInCage(16));
        assertTrue(ken.fitsInCage(36));
        assertTrue(ken.fitsInCage(24));
        assertFalse(ken.fitsInCage(18));
    }

    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
