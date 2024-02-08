# SaaSMonk Assignment
# Home page feature
java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class MovieReviewsTest {
    public static void main(String[] args) {
        // Set the path of the ChromeDriver executable
        
         System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");

        // Create a new instance of ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Navigate to the website
        driver.get("https://movie-reviews-psi.vercel.app/");

        // Test Case 1: Verify that the home page is displayed correctly
        String expectedTitle = "Movie Reviews";
        String actualTitle = driver.getTitle();
        if (actualTitle.equals(expectedTitle)) {
            System.out.println("Test Case 1: Passed");
        } else {
            System.out.println("Test Case 1: Failed");
        }

        // Test Case 2: Check if all the movies are visible on the page
        WebElement movieList = driver.findElement(By.className("movie-list"));
        if (movieList.isDisplayed()) {
            System.out.println("Test Case 2: Passed");
        } else {
            System.out.println("Test Case 2: Failed");
        }

       // Test Case 3: Verify that the search bar is clickable
        WebElement searchBar = driver.findElement(By.xpath("//input[@class='w-full  rounded-[4px] p-2 outline-none']")).click();
        if (searchBar.isEnabled()) {
            System.out.println("Test Case 3: Passed");
        } else {
            System.out.println("Test Case 3: Failed");
        }
     
        // Test Case 4: Test the search bar functionality
        String searchKeyword = "Oppenheimer";
        WebElement searchInput = driver.findElement(By.xpath("//input[@type='text']")).click();
        searchInput.sendKeys(Oppenheimer);
        
        WebElement searchResults = driver.findElement(By.xpath("//div[@class='relative']"));
        if (searchResults.getText().contains(searchKeyword)) {
            System.out.println("Test Case 3: Passed");
        } else {
            System.out.println("Test Case 3: Failed");
        }

        // Close the browser
        driver.quit();
    }
}

# Movie Review page 

public class MovieReviewsTest {
    public static void main(String[] args) {
        // Set the path of the ChromeDriver executable
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");

        // Create a new instance of ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Navigate to the website
        driver.get("https://movie-reviews-psi.vercel.app/");

        // Test Case 5: Click on a movie card oppenheimer and verify that the movie review page is displayed
        WebElement movieCard = driver.findElement(By.xpath("(//h1[@class='text-ellipsis text-lg'])[19]"));
        movieCard.click();
        WebElement movieReviewPage = driver.findElement(By.xpath("//h1[@class='text-2xl']"));
        if (movieReviewPage.isDisplayed()) {
            System.out.println("Test Case 5: Passed");
        } else {
            System.out.println("Test Case 5: Failed");
        }

        // Test Case 6: Verify if all the reviews for the selected movie are visible on the page
        WebElement reviewList = driver.findElement(By.xpath("//section[@class='mb-20 flex flex-col gap-10']"));
        if (reviewList.isDisplayed()) {
            System.out.println("Test Case 6: Passed");
        } else {
            System.out.println("Test Case 6: Failed");
        }

        // Close the browser
        driver.quit();
    }
}

# Adding movie and editing movie

public class AddMovieTest {
    public static void main(String[] args) {
        // Set the path of the ChromeDriver executable
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");

        // Create a new instance of ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Navigate to the website
        driver.get("https://movie-reviews-psi.vercel.app/");

        // Test Case 7: Add a new movie and verify that it is successfully added to the movie list
        WebElement addMovieButton = driver.findElement(By.xpath("//button[@class='flex w-fit items-center gap-1 rounded-md border-2 border-[#b5b4ef] bg-white px-2 py-1 text-[#6558f5] md:px-4 md:py-2']"));
        addMovieButton.click();

        WebElement movieTitleInput = driver.findElement(By.xpath("//input[@id='name']"));
        movieTitleInput.sendKeys("oppenheimer");

        // I added date of movie manually because inspect option was not available for calender

        WebElement movieTitleInput = driver.findElement(By.xpath("//button[@type='submit']")).click();

        String searchKeyword = "Oppenheimer";
        WebElement searchInput = driver.findElement(By.xpath("//input[@type='text']")).click();
        searchInput.sendKeys(Oppenheimer);
        
        WebElement searchResults = driver.findElement(By.xpath("//div[@class='relative']"));
        if (searchResults.getText().contains(searchKeyword)) {
            System.out.println("Test Case 7: Passed");
        } else {
            System.out.println("Test Case 7: Failed");
        }


        // Test Case 8: Verify that the new movie is visible on the home page

        Thread.sleep(2000);

        driver.navigate().refresh();

         String searchKeyword = "Oppenheimer";
          WebElement searchResults = driver.findElement(By.xpath("//div[@class='relative']"));
        if (searchResults.getText().contains(searchKeyword)) {
            System.out.println("Test Case 8: Passed");
        } else {
            System.out.println("Test Case 8: Failed");
        }
        

       
        // Test Case 10: Edit the details of an existing movie and verify that the changes are saved
        WebElement editButton = driver.findElement(By.xpath("//div[contains(text(),'New Movie')]/following-sibling::button[contains(text(),'Edit')]"));
        editButton.click();

        WebElement editTitleInput = driver.findElement(By.xpath("//input[@id='name']"));
        editTitleInput.clear();
        editTitleInput.sendKeys("Ford VS Ferrari_");

       
        WebElement UpdateButton = driver.findElement(By.xpath("//button[@type='submit']"));
        UpdateButton.click();


        // Close the browser
        driver.quit();
    }
}

# Adding review and editing review

public class AddReviewTest {
    public static void main(String[] args) {
        // Set the path of the ChromeDriver executable
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");

        // Create a new instance of ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Navigate to the website
        driver.get("https://movie-reviews-psi.vercel.app/");

         WebElement movieCard = driver.findElement(By.xpath("(//h1[@class='text-ellipsis text-lg'])[19]"));
        movieCard.click();
        WebElement movieReviewPage = driver.findElement(By.xpath("//h1[@class='text-2xl']"));

        //Test case- 13, Add a new review and verify that it is successfully added to the review list for that movie.

         driver.findElement(By.xpath("(//textarea[@id='review']")).click().clear();

         driver.findElement(By.xpath("//select[@id='movie']").sendkeys("Amazing movie");
         
         driver.findElement(By.xpath("//button[@type='submit']")).click();

         
        // Close the browser
        driver.quit();
    }
}

   # Delete movie

   public class DeleteMovieTest {
    public static void main(String[] args) {
        // Set the path of the ChromeDriver executable
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");

        // Create a new instance of ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Navigate to the website
        driver.get("https://movie-reviews-psi.vercel.app/");

        // Test case- 18, 19, 20 Delete a movie and verify that it is removed from the movie list.

        driver.findElement(By.xpath("(//div[@class='relative'])[12]"));
        
        driver.findElement(By.xpath("(//button[@class='rounded border border-[#a19fb6] p-1 shadow-sm'])[12]")).click();

        driver.navigate().refresh();
        
        Webelement DeletedMovie = driver.findElement(By.xpath("//input[@type='text']").sendkeys("Game of Thrones");
        
        
       if (DeletedMovie.isDisplayed()) {
            System.out.println("Test Case 18: Failed");
        } else {
            System.out.println("Test Case 18: Passed");
        } 

       
        // Close the browser
        driver.quit();
    }
}   






