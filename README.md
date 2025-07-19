# WordPress Custom Login Title

This code snippet allows you to **customize the title of your WordPress login page**. By default, the login page title usually displays "Log In" or "WordPress &lsaquo; Log In". This modification changes the title to show your site's name followed by a "⮜" symbol and then the default page title (e.g., "Your Site Name ⮜ Log In"). This helps in branding your login page and making it more identifiable.

## Why customize the login page title?

* **Branding:** Reinforces your site's brand even on the login screen.
* **Clarity:** Makes it immediately clear which site the user is logging into, especially if they manage multiple WordPress installations.
* **Professionalism:** Adds a polished touch to your WordPress installation.

## Installation

You have two primary methods to implement this code:

### Method 1: As a Standalone Plugin (Recommended)

Creating a small, dedicated plugin is the most robust way to add this customization. It ensures your custom title remains active even if you switch themes.

1.  Create a new folder named `wp-custom-login-title` inside your WordPress site's `wp-content/plugins/` directory.
2.  Inside this new folder, create a file named `wp-custom-login-title.php`.
3.  Copy and paste the following code into `wp-custom-login-title.php`:

    ```php
    <?php
    /**
     * Plugin Name: WordPress Custom Login Title
     * Description: Customizes the title of the WordPress login page to include your site's name.
     * Version: 1.0
     * Author: Your Name (Optional)
     */

    function custom_admin_login_title($admin_title, $title) {
        return get_bloginfo('name') . ' ⮜ ' . $title;
    }
    add_filter('login_title', 'custom_admin_login_title', 10, 2);
    ?>
    ```

4.  Go to your WordPress admin dashboard, navigate to **"Plugins"**, and **activate** the "WordPress Custom Login Title" plugin.

### Method 2: Adding to your Theme's functions.php File

You can add this code directly to your active theme's `functions.php` file. **Before doing so, it's highly recommended to back up your `functions.php` file.**

1.  Navigate to `wp-content/themes/YourThemeName/` (replace `YourThemeName` with the actual name of your active theme).
2.  Open the `functions.php` file.
3.  Add the following code to the end of the file (before the closing `?>` tag, if one exists):

    ```php
    function custom_admin_login_title($admin_title, $title) {
        return get_bloginfo('name') . ' ⮜ ' . $title;
    }
    add_filter('login_title', 'custom_admin_login_title', 10, 2);
    ```

## Customization

The current code uses `get_bloginfo('name')` to fetch your site's title. You can modify the return string to anything you prefer. For example:

* **To just show your site name:**
    ```php
    return get_bloginfo('name');
    ```
* **To show a custom text before the original title:**
    ```php
    return 'Welcome to My Site' . ' ⮜ ' . $title;
    ```
* **To show only a specific custom text:**
    ```php
    return 'My Company Login';
    ```

## Contributing

Your contributions are welcome! If you have suggestions or improvements for this code, feel free to open a "Pull Request" or report an "Issue."

## License

This project is licensed under the MIT or later.
