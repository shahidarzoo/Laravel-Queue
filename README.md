# Laravel-Queue
### LINKS

[https://appdividend.com/2017/12/21/laravel-queues-tutorial-example-scratch/](https://appdividend.com/2017/12/21/laravel-queues-tutorial-example-scratch/)
### Run these artisan command
```php
php artisan queue:table

php artisan migrate

php artisan make:job SendEmailJob

```
### Before Submit Data open cmd and run
```php

php artisan queue:work --queue=your queue name --tries=3

```

### Check Logs
```php
cd storage/logs/
nano laravel-2019-05-15.log
```
### Add this in Controller
```php
use App\Jobs\NotificationJob;

 NotificationJob::dispatch($request->audience, $request->title, $request->description)
 ->onQueue('notification')->delay(Carbon::now()->addSeconds(3));
```

### App\Jobs

```php
 protected $type;
    protected $title;
    protected $description;
    public function __construct($type, $title, $description)
    {
        $this->type = $type;
        $this->title = $title;
        $this->description = $description;
    }


```
