tp60unit , unit test for thinkphp6.0, only test
==

test thinkphp6.0 app's logic by phpstorm 2020

**usage**
    
    composer require wsteel/php60unit

**require**
    
    "php": ">=7.2.0",
    "topthink/framework": "6.0.*"
    "phpunit/phpunit": "8.*"

**phpstorm setting**

File | Settings | Languages & Frameworks | PHP | Test Frameworks

    PHPUnit library -> Path to phpunit.phar -> _YOUR_phpunit-*.phar

**demo**

filename

    tests/demo/demoTest.php

content
```php

namespace tests\demo;

use wsteel\tp60unit\TestCase;

class demoTest extends TestCase
{

    public function testTrue()
    {
        $this->assertTrue(true);
    }

    public function testFalse()
    {
        $this->assertFalse(false, 'false');
    }


    public function testModel()
    {
        $e = \app\model\User::find(1);
        dump($e);
        $this->assertNotEmpty($e);
    }

    public function testDB()
    {
        $user = Db::name('user');
        $e = $user->where('id', '=' ,1)->select();
        dump($e);
        $this->assertNotEmpty($e);
    }

    public function testConfig()
    {
        $config = config('database');
        dump($config);
        $this->assertNotEmpty($config);
    }
}

```