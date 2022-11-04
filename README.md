# lab2b-part1
# code



    int main() {

      const uint BOOT_PIN = 21;
      gpio_init(BOOT_PIN);
      gpio_set_dir(BOOT_PIN, GPIO_IN);
      //set_sys_clock_48();
      stdio_init_all();
      printf("WS2812 Smoke Test, using pin %d", WS2812_PIN);

      // todo get free sm
      PIO pio = pio0;
      int sm = 0;
      uint offset = pio_add_program(pio, &ws2812_program);
      turn_on_NeoPixel_power();
      ws2812_program_init(pio, sm, offset, WS2812_PIN, 800000, IS_RGBW);

      //int t = 0;
       uint32_t pixel_grb = 0x00000000;
      while (1) {
          if(!gpio_get(BOOT_PIN)) {
              put_pixel(0X0FFFFFFF);
          } else {
              put_pixel(0x00000000);
          }
          sleep_ms(100);

        
      }
    }

# light

![image](https://github.com/sudong-wang/lab2b-part1/blob/main/7bspa-at7xj.gif)
