import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up some constants
WIDTH, HEIGHT = 640, 480
CAR_WIDTH, CAR_HEIGHT = 50, 50
SPEED = 5

# Set up some variables
car_x, car_y = WIDTH / 2, HEIGHT / 2
car_velocity = 0

# Create the game window
screen = pygame.display.set_mode((WIDTH, HEIGHT))

# Game loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Get a list of all keys currently being pressed down
    keys = pygame.key.get_pressed()

    # Move the car based on the keys being pressed
    if keys[pygame.K_UP]:
        car_velocity = -SPEED
    elif keys[pygame.K_DOWN]:
        car_velocity = SPEED
    else:
        car_velocity = 0

    car_y += car_velocity

    # Draw everything
    screen.fill((0, 0, 0))
    pygame.draw.rect(screen, (255, 0, 0), (car_x, car_y, CAR_WIDTH, CAR_HEIGHT))

    # Update the display
    pygame.display.flip()

    # Cap the frame rate
    pygame.time.Clock().tick(60)

